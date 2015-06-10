# Primeras líneas de los fuentes Javascript

Todos nuestros fuentes Javascript que estén diseñados tanto para usarse en Node como en el Navegador deberían empezar así:

```js
"use strict";
(function webpackUniversalModuleDefinition(root, factory) {
    /* istanbul ignore next */
    if(typeof exports === 'object' && typeof module === 'object')
        module.exports = factory();
    else if(typeof define === 'function' && define.amd)
        define(factory);
    else if(typeof exports === 'object')
        exports["nombreDelModulo"] = factory();
    else
        root["nombreDelModulo"] = factory();
})(this, function() {

var nombreDelModulo = {};

nombreDelModulo.ejemploDeFuncion = function ejemploDeFuncion(){
  // ...
};

// ...
// ...

});

```

Cuando sean solo para el Node o solo para el navegador no hace falta y no lo hacemos para no confundir. 
