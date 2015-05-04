Para recuperarse del error (por ejemplo si no se puede parsear el JSON levanta el servidor con valores por defecto y avisa en el log):

```js
readAndParseJsonFile('config.json',function(err, config){
    if(err){
        console.log('no encuentro la configuracion uso el valor por defecto');
        config = defaultConfig;
    }
    try{
        startServer(config.host, config.port);
    }catch(err){
        console.log('error al levantar servidor',err);
    }
});

```

Con promesas:

```js
readAndParseJsonFile('config.json').catch(function(err){
    console.log('no encuentro la configuracion uso el valor por defecto');
    return defaultConfig;
}).then(function(config){
    startServer(config.host, config.port);
}).catch(function(err){
    console.log('error al levantar el servidor',err);
});

```
