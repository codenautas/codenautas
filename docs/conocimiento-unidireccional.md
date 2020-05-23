<!--multilang v0 es:conocimiento-unidireccional.md en:one-way-knowing.md -->

<!--lang:es-->

# Conocimiento unidireccional

Para mantener la simplicidad del desarrollo de sistemas (por ejemplo [KISS](https://en.wikipedia.org/wiki/KISS_principle)) 
se puede usar la regla de conocimiento unidireccional. 
Si bien no es una regla obligatoria, ni garantiza la simplicidad puede ayudar a ordenar el diseño y el código.

<!--lang:en--]

# Knowing One Direction

🦆

[!--lang:*-->

<!--multilang buttons-->

idioma: ![castellano](https://raw.githubusercontent.com/codenautas/multilang/master/img/lang-es.png)
también disponible en:
[![inglés](https://raw.githubusercontent.com/codenautas/multilang/master/img/lang-en.png)](one-way-knowing.md)


<!--lang:es-->

# Conocimiento

<!--lang:en--]

# Knoweldge

[!--lang:es-->

En este contexto vamos a usar conocimiento en el sentido de conocer a alguien o algo, tener acceso a él. 
En particular en un sistema decimos que A conoce a B sí:

<!--lang:en--]

[!--lang:es-->

   1. A es una función o procedimiento que puede invocar al procedimieto o función B: `function A(){ B(); }`
   2. A es una tabla con una foreign key hacia B: `alter table A add foreign key (id_B) references B(id)`
   3. Un tipo A es construido utilizando un tipo B: `type A = { n:number }; type B = { a:A }`
   4. Código en la carpeta A puede incluir código de la carpeta B: `import { bCode } from '../b/code'`

<!--lang:en--]

[!--lang:es-->

## Sistemas complejos

<!--lang:en--]

## Complex system

[!--lang:es-->

A veces el modelo del problema (modelo del negocio) no es tan simple como para bancarse esa restricción. 
Lo que hay uno tendría que lograr es que el programa que uno hace sí se lo banque.

<!--lang:en--]

[!--lang:es-->

## Ejemplo con tablas de la base de datos

<!--lang:en--]

## Database table example

[!--lang:es-->

Tomemos como ejemplo la tabla países y la tabla ciudades. 
Cada ciudad está en un país y va a tener una FK que referencie al país donde pertenece. 
En *[backend-plus](https://github.com/codenautas/backend-plus/blob/master/LEEME.md)*
las definiciones de tabla incluyen una lista de `"detailTables"` 
para que al momento de dibujar la tabla aparezcan unas flechitas para acceder a las tablas detalles (unidas por su FK).
En este caso la tabla países tiene como una de sus `detailTables` a ciudades y 
*[backend-plus](https://github.com/codenautas/backend-plus/blob/master/doc/definicion-tablas.md)*
al mostrar la tabla paises pondrá una flechita para mostrar todas las ciudades del país (relacionadas por código de país). 

<!--lang:en--]

In *[backend-plus](https://github.com/codenautas/backend-plus)* ...

*[backend-plus](https://github.com/codenautas/backend-plus/blob/master/doc/table-definitions.md)* ...

[!--lang:es-->

Es cierto que es más eficiente que *backend-plus* le pregunte a la tabla países cuáles son sus `"detailTables"`,
sería molesto preguntarle a todas las tablas si alguna es detalla de países para enterarse que ciudad lo es. 
Pero hay otra solución, como ciudades conoce a paises, ciudades podría tener en su definición `"iAmDetailOf": ["paises"]` 
y al momento de levantar el sistema, el backend podría recorrer todas las tablas una sola vez 
y cuando encuentra "iAmDetailOf" registra en la tabla destino que tal tabla es su hija. 

<!--lang:en--]

[!--lang:es-->

Eso tiene un defecto, y es que para el programador es cómodo saber, cuando está escribiendo algo de países quienes son todos sus `detailTables`. 
Por un lado eso es imposible si hay stack de aplicaciones (pero supongamos que no lo hay y 
que querramos ver todos los details de operativos escritos en un solo lugar porque comunicativamente entre programadores eso conviene). 
Si queremos seguir usando `"detailTables"` con la lista la solución es tener dos capas de definición de tablas, 
la definición física, y la definición de presentación, en la definición física las tablas solo conocen sus tablas padre, 
en la definición de presentación (que es otro .ts) cada .ts de definición conoce a todas las tablas físicas 
y a las definiciones de presentación de sus padres.

<!--lang:en--]

[!--lang:es-->

## Ejemplo con carpetas de código

<!--lang:en--]

## Code folders example

[!--lang:es-->

Primero deberíamos preguntarnos por qué tenemos el código separado en carpetas. 
Una posibilidad es para separar subsistemas, módulos, namespaces o clases. En este caso es claro se aplica la regla de conocimiento entre objetos.

Otra posibilidad es separar en función de si es código que será enviado al cliente (a todos o los que estén logueados),
código que va a correr en el servidor de producción, herramientas de mantemiento y testing. 

<!--lang:en--]

[!--lang:es-->

Imagienos código typescript organizado en las siguientes carpetas:

<!--lang:en--]

[!--lang:*-->

```
./src
   - /unlogged
   - /client
   - /server
   - /mant
   - /test
```

<!--lang:es-->

Lo lógico que es que el código de `unlogged` no conozca nada del resto del código porque al correr en el cliente para cualquier usuario
no tendría por qué tener más conocimiento que lo que se necesita para correr lo de un usuario que sí se logueó y obviamente va a tener más opciones. 
Entonces en vez de tener una carpeta `/common` o combinaciones de common 
la idea es poner lo común que haya entre dos carpetas en la carpeta más conocida (la que está más arriba).

Por ejemplo `/test` tiene que conocer a todos porque tiene que poder probar todo el código. 
Ninguna otra necesita conocer los `/test` salvo que esté haciendo desarrollo. 
El sistema entero debería poder instalarse sin la carpeta `/test`.

<!--lang:en--]

[!--lang:es-->

## Conocimiento fraternal

<!--lang:en--]

## Siblings knowing each other

[!--lang:es-->

La restricción es si A conoce a B, B no puede conocer a A (salvo contadísimas excepciones de hermanos puros, donde A y B se pueden conocer entre sí si conocen a los mismos y son conocidos por los mismos, pero esta excepción raramente es necesaria).

<!--lang:en--]

[!--lang:*-->
