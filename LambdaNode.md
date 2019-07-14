1. Code proposed by aws example  
    
```javascript
exports.handler = async (event) => {  
    // TODO implement  
    const response = {  
        statusCode: 200,  
        body: JSON.stringify('Hello from Lambda!'),  
    };  
    return response;  
};  
```    

2. Exporting a method with the handler. in this case the method is changed from .handler to .first and it has to be changed also in the handler, which changes from index.handler to index.first   
Console.log will give the output of the function  
Context.done will return the informations to THE LOGS.   
The test event is not important since we're not using the input in this specific call.  


```javascript
exports.first = function(event, context) {

    console.log('Hello FROM CONSOLE');
    
    // TODO implement
    context.done(null, 'Hello FROM CONTEXT');
};
```

3. Exporting errors with the function context.done.  
In previous example, the context.done returns the null value. It could have reported an error, and in the following case there is the possibility that some calculations gets an error and return an error, as displayed.  
Try the function with the right sum value = 15 and with a wrong value = 16. 
This function is useful when we want to send the log in some specific context, like an alerting function on slack or other systems.   

```javascript
exports.first = function(event, context) {

    console.log('Hello FROM CONSOLE');
    let a = 5;
    let b = 10;
    const c = a + b;
    
    if(c === 16) {
        // TODO implement
    context.done(null, c);
    } else {
    context.done("error of the expected function");
    }
};
```
  
4. This example returns a quote from forismatic. Context.done will return the information at the end of the thread.    
  
```javascript
const http = require('http');

exports.first = function(event, context) {
    
    http.get('http://api.forismatic.com/api/1.0/json?method=getQuote&lang=en&format=json',res => {
        
        let rawData = '';
        res.on('data', (chunk) => { rawData += chunk;});
        
        res.on('end', () => {
            context.done(null, rawData);  
        });
    });  
};   
```

5. This example demonstrates what happens when a lambda has a duration longer than the timeout set by default. Default timeout is 3s, while here the lambda will last 5s.  
  
```javascript
const http = require('http');

exports.first = function(event, context) {
    
  setTimeout(function() {
     context.done(null, "done");
  }, 5000)   
     
};   
```


6. <b>Callback</b> This example demonstrates what happens when a lambda has a duration longer than the timeout set by default. Default timeout is 3s, while here the lambda will last 5s.  
The <i>callbackWaitsForEmptyEventLoop</i> can be set to true or false and that changest the way the eventloop waits for the finish of the 10s. 
  
```javascript
exports.first = function(event, context, callback) {
    
  context.callbackWaitsForEmptyEventLoop = true;
  
  setTimeout(function() {
     console.log('Hello, World!');
  }, 10000)   
     
 callback(null, 'I am done');
};   
```


6. <b>callback vs context.done method comparison</b>.  
Both methods have two values, the error and the output.  
context methods are legacy methods and have been deprecated in 2017. 
  
```javascript
exports.first = function(event, context, callback) {
    
  context.callbackWaitsForEmptyEventLoop = true;
  
  setTimeout(function() {
     console.log('Hello, World!');
  }, 10000)   
     
 context.done(null, 'I am done');
 
 callback(null, 'I am done');
};   

7. <b>Null</b>

```javascript
exports.first = function(event, context, callback) {
};  
```

8. <b>Response for an API Gateway</b> The response is done via an object. This is done with an object.  
```javascript
exports.first = function(event, context, callback) {

    callback(null, {
        "key": "some data"
    });
    
};  
```
