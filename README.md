# node-mocker-recorder


```
var cache = {};

// response from cache...
app.use(function(req, res, next){
    req.final_input_json = req.originalUrl + '.' + JSON.stringify(req.body);
    if(cache[req.final_input_json]){
        // response from cache
        console.log('response from cache', req.final_input_json)
        res.json(cache[req.final_input_json]);
    } else {
        next();
    }
});




// record response
app.use(function(req, res, next){
    cache[req.final_input_json] = req.final_resp;
    console.log('Record', req.final_input_json, req.final_resp);
    res.json(req.final_resp);
});
```
