# Primeras líneas de los fuentes Javascript

Todos nuestros fuentes Javascript que estén diseñados tanto para usarse en Node como en el Navegador deberían empezar así:

```js
"use strict";
/* eqnull:true */
(function webpackUniversalModuleDefinition(root, factory) {
    /* global define */
    /* global globalModuleName */
    /* istanbul ignore next */
    if(typeof root.globalModuleName !== 'string'){
        root.globalModuleName = factory.name;
    }
    /* istanbul ignore next */
    if(typeof exports === 'object' && typeof module === 'object')
        module.exports = factory();
    else if(typeof define === 'function' && define.amd)
        define(factory);
    else if(typeof exports === 'object')
        exports[root.globalModuleName] = factory();
    else
        root[root.globalModuleName] = factory();
    root.globalModuleName = null;
})(this, function nombreDelModulo() {

var nombreDelModulo = {};

nombreDelModulo.ejemploDeFuncion = function ejemploDeFuncion(){
  // ...
};

// ...
// ...

return nombreDelModulo;

});

```

Cuando sean solo para el Node o solo para el navegador no hace falta y no lo hacemos para no confundir. 
