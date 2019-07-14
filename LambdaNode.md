Code proposed by aws example  
    
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

Exporting a method with the handler. in this case the method is changed from handler to first and it has to be changed also in the handler, which changes from index.handler to index.first.  
Console.log will give the output of the function
Context.done will return the informations to THE LOGS
The test event is not important since we're not using the input in this specific call


```javascript
exports.first = function(event, context) {

    console.log('Hello FROM CONSOLE');
    
    // TODO implement
    context.done(null, 'Hello FROM CONTEXT');
};
```
