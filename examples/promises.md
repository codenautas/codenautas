Sin usar promesas, usando callbacks puros:

```js
var fs = require('fs');

function readAndParseJsonFile(filename,callback){
    fs.readFile(sanitizeFileName(filename),{encoding:'utf8'},function(err, stringData){
        if(err){
            callback(err);
        }else{
            try{
                var parsedData=JSON.parse(stringData);
                // acá no se puede llamar al callback para que no esté dentro del try
            }catch(parseError){
                callback(parseError);
                return ; // acá debo terminar para no llamar al otro callback
            }
            callback(null, parsedData);
        }
    });
}

readAndParseJsonFile('config.json',function(err, config){
    if(err){
        console.log('error al levantar servidor',err);
    }else{
        try{
            startServer(config.host, config.port);
        }catch(err){
            console.log('error al levantar servidor',err);
        }
    }
});
```

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
}).catch(function(err){
    console.log('error al levantar el servidor',err);
});
```

 * ver ejemplo con recuperación del estado del error [acá](promises-recup.md)

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

## casos de prueba

Imaginemos que queremos probar la función f que devuelve una promesa. Puedo querer verificar que la cadena de promesas que devuelve f finalmente se resuelve con cierto valor, o puedo querer verificar que termina con cierto error

### prueba de promesa bien resuelta

```js
var expect = require('expect.js');
// ...
it('esta prueba asincrónica... ', function(done){ // "done" porque es asincrónica
    // ...
    f(...).then(function(respuestaObtenida){
        expect(respuestaObtenida).to.eql(valorEsperado);
        done(); // sin parametros=termino ok
    }).catch(function(err){
        done(err);
    });
});
```

### prueba de promesa que espero que devuelva una falla
```js
it('esta prueba asincrónica... ', function(done){
    f(...).then(function(respuestaObtenida){
        done("no esperaba una respuesta, esperaba un error y obtuve "+respuestaObtenida);
    }).catch(function(err){
        expect(err).to.be(Error);
        expect(err.message).to.match(/parte del mensaje que esperaba/);
        done(); // sin parametros=termino ok
    });
});
```
