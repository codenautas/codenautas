# Links

## a la documentación sobre los paquetes que usamos:

 * **File System**: Uamos [fs-promise](https://www.npmjs.com/package/fs-promise), 
 la documentación está *prometizada* en [fs](https://nodejs.org/api/fs.html) 
 y en [fs-extra](https://www.npmjs.com/package/fs-extra) (que hay que incluirlo antes de fs-promise para que se pueda usar)
 * **Base de datos**: Usamos solamente postgres, 
 accedemos con nuestra librería [pg-promise-strict](https://www.npmjs.com/package/pg-promise-strict)
 que está *prometizada* en [pg](https://www.npmjs.com/package/pg), 
 cuya documentación está en [pg-wiki](https://github.com/brianc/node-postgres/wiki)
 * **Promesas**: Usamos nuestro [best-promise](https://www.npmjs.com/package/best-promise), 
 basado en [any-promise](https://www.npmjs.com/package/any-promise). Para entender cómo se usa se puede leer
   * [html5rocks](http://www.html5rocks.com/en/tutorials/es6/promises/), en inglés una explicación larga con motivación
   * [ejemplos](https://github.com/codenautas/codenautas/blob/master/examples/promises.md) nuestros sobre cómo las usamos
 * **HTML**: 
   * Si lo escribimos a mano lo hacemos con sitnaxis [jade](http://jade-lang.com/) 
   que se renderiza con el paquete [jade](https://www.npmjs.com/package/jade)
   * Si lo generamos usamos nuestra librería [js-to-html](https://www.npmjs.com/package/js-to-html)
   * Para usar CSS usamos [stylus](https://learnboost.github.io/stylus/)
 * **las pruebas**: 
   * Los casos los escribimos con [mocha](http://mochajs.org/),
   * las comparaciones con [expect.js](https://www.npmjs.com/package/expect.js)
   * para la cobertura de código usamos [istambul](https://www.npmjs.com/package/istanbul)
   * para las *funciones mock* o espías usamos [expect-called](https://www.npmjs.com/package/expect-called)
   * para mostrar información de fecha/hora en los logs usamos [console-stamp](https://www.npmjs.com/package/console-stamp)
 * **la configuración** la ponemos en formato [yaml](http://www.yaml.org/spec/1.2/spec.html#id2759963) 
 y lo leemos con [read-yaml-promise](https://www.npmjs.com/package/read-yaml-promise),
   * si tenemos algún archivo de configuración en json lo leemos con la función `fs.readJson`
   * los nombres de archivos que empiezan con `local` deberían estar siempre excluidos del repositorio 
   (o sea debe incluirse `local-*` y `*-local.*` en `.gitignore`
 * **la documentación** la escribimos en [MarkDown](https://guides.github.com/features/mastering-markdown/), 
 si lo que documentamos tiene como objetivo compartirse con la comunidad tratamos de escribirlo en inglés y castellano 
 usando nuestra librería [multilang](https://www.npmjs.com/package/multilang).
 * **el formato** de la información que desplegamos se basa en:
   * [moment](http://momentjs.com/docs/) para fechas
   * [numeral](http://numeraljs.com/) para números
