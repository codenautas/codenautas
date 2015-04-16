# cucardas de codenautas

La mayoría del código que hagamos (salvo que haya una buena razón para no hacerlo) va a tener las siguientes cucardas

imagen | **código** | **notas**
-------|------------|-----------
![designing](https://img.shields.io/badge/stability-desgining-red.svg) | `![designing](https://img.shields.io/badge/stability-desgining-red.svg)` | opt. manual
![extending](https://img.shields.io/badge/stability-extending-orange.svg) | `![designing](https://img.shields.io/badge/stability-extending-orange.svg)` | opt. manual
![npm-version](https://github.com/codenautas/codenautas/blob/master/img/npm-version.png) | `![version][ https://img.shields.io/npm/v/multilang.svg?style=flat](https://npmjs.org/package/multilang)`  | 
![medalla-linux](https://github.com/codenautas/codenautas/blob/master/img/medalla-ejemplo-linux.png)       | `![linux][https://img.shields.io/travis/xxx/yyy/master.svg?label=linux&style=flat](https://travis-ci.org/xxx/yyy)`  | la cambiaría por Build
![medalla-dependencias](https://github.com/codenautas/codenautas/blob/master/img/medalla-ejemplo-dependencies.png)       | `[![dependencies](https://david-dm.org/xxx/yyy.svg)](https://david-dm.org/xxx/yyy)` | falta

## referencias sobre la tabla:
 * **código** va tal cual salvo por los siguientes parámetros que hay que reemplazar
   * **own** el nombre del repositorio, en nuestro caso *codenautas*
   * **mod** el nombre del módulo
 * notas
   * **opt.** la cucarda es optativa según el caso:
     * **designing** cuando todavía no sabemos qué forma va a tener, estamos en etapa de diseño, no están definidos los parámetros ni nada; probablemente el módulo todavía no esté usado por ningún otro. Debería ser versión 0.0.x
     * **extending** cuando las intefaces del API están relativamente diseñadas (aún pueden cambiar bastante porque no está estable). Todavía falta agregar mucha funcionalidad, pero lo que está se puede usar porque tiene casos de prueba. Debería ser versión 0.x.x
     * **stable** no ponemos nada (solo quitamos las otras cucardas de estabilidad) 
  * **manual** la cucarda se debe ponerse o quitarse manualmente (las demás son automáticas). 