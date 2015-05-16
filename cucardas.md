# cucardas de codenautas

La mayoría del código que hagamos (salvo que haya una buena razón para no hacerlo) va a tener las siguientes cucardas

imagen | **código** | **notas**
-------|------------|-----------
![designing](https://img.shields.io/badge/stability-desgining-red.svg) | `![designing](https://img.shields.io/badge/stability-desgining-red.svg)` | opt. manual
![extending](https://img.shields.io/badge/stability-extending-orange.svg) | `![extending](https://img.shields.io/badge/stability-extending-orange.svg)` | opt. manual
![npm-version](https://raw.githubusercontent.com/codenautas/codenautas/master/img/npm-version.png) | `[![version](https://img.shields.io/npm/v/yyy.svg)](https://npmjs.org/package/yyy)`  |
![downloads](https://raw.githubusercontent.com/codenautas/codenautas/master/img/downloads.png) | `[![downloads](https://img.shields.io/npm/dm/yyy.svg)](https://npmjs.org/package/yyy)`|
![build](https://raw.githubusercontent.com/codenautas/codenautas/master/img/medalla-ejemplo-linux.png)       | `[![build](https://img.shields.io/travis/xxx/yyy/master.svg)](https://travis-ci.org/xxx/yyy)`  | linux/build
![windows](https://raw.githubusercontent.com/codenautas/codenautas/master/img/windows.png)   |   `[![windows](https://img.shields.io/appveyor/ci/xxx/yyy/master.svg?label=windows&style=flat)](https://ci.appveyor.com/project/xxx/yyy)`  | casos especiales
![coverage](https://raw.githubusercontent.com/codenautas/codenautas/master/img/coverage.png)   |   `[![coverage](https://img.shields.io/coveralls/xxx/yyy/master.svg)](https://coveralls.io/r/xxx/yyy)`  |
![climate](https://raw.githubusercontent.com/codenautas/codenautas/master/img/climate.png)   | `[![climate](https://img.shields.io/codeclimate/github/xxx/yyy.svg)](https://codeclimate.com/github/xxx/yyy)` |
![dependencias](https://raw.githubusercontent.com/codenautas/codenautas/master/img/medalla-ejemplo-dependencies.png) | `[![dependencies](https://img.shields.io/david/xxx/yyy.svg)](https://david-dm.org/xxx/yyy)` | 

## referencias sobre la tabla:
 * **código** va tal cual salvo por los siguientes parámetros que hay que reemplazar
   * **xxx** el nombre del repositorio, en nuestro caso *codenautas*
   * **yyy** el nombre del módulo
 * notas
   * **opt.** la cucarda es optativa según el caso:
     * **designing** cuando todavía no sabemos qué forma va a tener, estamos en etapa de diseño, no están definidos los parámetros ni nada; probablemente el módulo todavía no esté usado por ningún otro. Debería ser versión 0.0.x
     * **extending** cuando las intefaces del API están relativamente diseñadas (aún pueden cambiar bastante porque no está estable). Todavía falta agregar mucha funcionalidad, pero lo que está se puede usar porque tiene casos de prueba. Debería ser versión 0.x.x
     * **stable** no ponemos nada (solo quitamos las otras cucardas de estabilidad) 
   * **manual** la cucarda se debe ponerse o quitarse manualmente (las demás son automáticas). 
   * **casos especiales** la cucarda solo se pone en ciertos casos (ej: windows se pone cuando podría ser distinto el comportamiento en windows que en linux).
   Si el proyecto tiene el archivo appveyor.yaml la cucarda de windows debe quedar.
   * **linux/build** irá linux o buid en función de si está la cucarda de windows o no.
