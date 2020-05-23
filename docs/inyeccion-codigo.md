<!--multilang v0 es:inyeccion-codigo.md en:codeInjection.md -->

<!--lang:es-->

# Inyección de código

> **Nunca armes código dentro de una variable de texto mezclando instrucciones y datos** para ningún tipo de lenguaje de ningún level: SQL, Javascript, HTML, CSS, JSON, yaml, etc...

<!--lang:en--]

# Code injection

> **Never, build ANY code by adding strings that contents data with strings that content code** of any language at any level: SQL, Javascript, HTML, CSS, JSON, yaml, etc...

[!--lang:*-->

<!--multilang buttons-->

idioma: ![castellano](https://raw.githubusercontent.com/codenautas/multilang/master/img/lang-es.png)
también disponible en:
[![inglés](https://raw.githubusercontent.com/codenautas/multilang/master/img/lang-en.png)](codeInjection.md)


<!--lang:es-->

## ¿Qué son datos?

<!--lang:en--]

## What is data?

[!--lang:es-->

Datos (en este contexto) es cualquier valor o información que sea introducida o modificada por algún usuario ahora o en el futuro (pensando en el ciclo de vida del proyecto).

<!--lang:en--]

Data is any value that is introduced or edited by the user now or in the future (thinking in the life cycle of the project).

[!--lang:es-->

### ¿Cómo introduce o modifica datos un usuario?

<!--lang:en--]

### How a user introuce or edit data?

[!--lang:es-->
  1. en algún campo (`input`) de un formulario en alguna página del sistema
  2. en un valor guardado en la base de datos en el que el usuario tenga permiso de escribir 
     (aún cuando el sistema tome los datos después desde la base de datos esos datos llegaron ahí porque algún usuario los cargó)
  3. en la dirección `URL` de cualquier `get` o `post` (o el método que sea)
  4. en cualquier clase de archivo subido que después sea procesado por el backend

<!--lang:en--]

  1. In a `input` field in a web page 
  2. In a value stored in the database when it has writes to write. 
  3. In a `URL` that get, post data to the backend (may be delete or any of the http methods)
  4. In any kind of files uploaded to the backend and then proccesed by it

[!--lang:es-->

### Qué significa pensar en el futuro?

<!--lang:en--]

### What means thinking in the future?

[!--lang:es-->

Supopnga que la definición del problema dice 
*el sistema tiene que establecer el valor de A como máximo al doble de B*. Se puede escribir algo así:

<!--lang:en--]

Supouse that the definition of the problem says 
*the system must set a maximum to A which is twice that of B*. You can write this:

[!--lang:*-->

```js
const COEF_A_B=2;

await query('update t1 set A = min($1, '+COEF_A_B+' * B)) where...', [params.requested_a]);
```

<!--lang:es-->

Ese código es seguro hoy, porque `COEF_A_B` es una constante numérica que nadie puede editar.
Pero en un futuro podrían agregar muchas líneas de código entre `const` y `query`.
Más adelante alguien podría decidier que `COEF_A_B` va a estar almacenado en la base de datos 
para que un usuario autorizado pueda editar ese valor. 
Entonces el código pasaría a ser inseguro. 

En mi opinión el código era inseguro desde el primer momento

<!--lang:en--]

That is safe today, because `COEF_A_B` is a numeric constant that the user cannot edit. 
But int the future many lines could be added between `const` and `query`. 
Later someone can decide that `COEF_A_B` may be stored in the database and edited by a manager. 
Then the code becomes unsafe. 

In my opinion the code was unsafe from the beginning.

[!--lang:es-->

## inyección de código en SQL

<!--lang:en--]

## code injection in SQL

[!--lang:es-->

¿Cómo evitarlo?

> **Nunca arme código SQL en una variable `string` mezclando instrucciones y datos**

<!--lang:en--]

How to avoid it?

> **Never, build SQL code by adding strings that contents data**

[!--lang:es-->

Si se puede envíe los datos separados de las instrucciones. 
En general todas las librerías y métodos de acceso a la base de datos lo permiten. 

<!--lang:en--]

If you can, send the data separately.

[!--lang:*-->

```js
⛔ await query("update t1 set c1='"+v1+"'") 
👍 await query("update t1 set c1 = $1", [v1])
```

<!--lang:es-->

Si no se puede, por ejemplo porque es necesario armar código SQL muy largo lo que se debe hacer es escapar los datos antes de mezclarlos.

<!--lang:en--]

If you can't send the data separately, i.e. you need to build a large sql programmatically quote the data.

[!--lang:es-->

Armando instruccioens SQL en Javascript:

<!--lang:en--]

Building it in Javascript:

[!--lang:*-->

```js
⛔ "update t1 set c1='"+v1+"'" 
⛔ `update t1 set c1='${v1}'`
👍 "update t1 set c1="+quoteLiteral(v1)
👍 `update t1 set c1 = ${quoteLiteral(v1)}`
  
⛔ 'update "'+t1+'" set c1 = null'
⛔ `update "${t1}" set c1 = null`
👍 'update '+quoteIdent(t1)+' set c1 = null'
👍 `update ${quoteIdent(t1)} set c1 = null`
```

<!--lang:es-->

## inyección de código en jQuery

<!--lang:en--]

## code injection in jQuery

[!--lang:es-->

¿Cómo evitarlo?

> **Nunca arme código HTML en una variable `string` mezclando tags y datos**

<!--lang:en--]

How to avoid it?

> **Never, build HTML code by adding strings that contents data**

[!--lang:*-->

```js
⛔ $('#id').html('<p>'+value+'</p>')
👍 $('#id').append($('<p>').text(value))

⛔ $('#id').html('<img src="'+url+'">')
👍 $('#id').append($('<img>').attr('src',url))
```