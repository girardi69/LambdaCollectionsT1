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

```javascript
exports.first = function(event, context) {

    console.log('FROM CONSOLE');
    
    // TODO implement
    context.done(null, 'Hello FROM CONTEXT');
};
```
