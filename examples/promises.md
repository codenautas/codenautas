Uso típico de promesas:

```js
var fs=require('fs-promise');

function readAndParseJsonFile(filename){
    return fs.readFile(sanitizeFileName(filename),{encoding:'utf8'}).then(function(content){
        return JSON.parse(content);
    });;
}

readAndParseJsonFile('config.json').then(function(config){
    startServer(config.host, config.port);
});
```

Preferimos en las primeras líneas de readAndParse poner:
```js
function readAndParseJsonFile(filename){
    return Promise.resolve().then(function(){
        return fs.readFile(sanitizeFileName(filename),{encoding:'utf8'});
    }).then(function(content){
        return JSON.parse(content);
    });
}
```

que tiene la ventaja de que si `sanitizeFileName` tira una excepción se puede capturar dentro de la cadena de excepciones con un `.catch`
