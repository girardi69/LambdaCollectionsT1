## This function is combined with the AWS API GW and returns the response with html  

```javascript

let i = 1;

exports.fi = function(event, context, callback) {

    console.log(i++);
    
  

    var html = '<html><head><title>HTML from API Gateway/Lambda</title></head>' + 
        '<body><h1>This is the Udemy Example API with external initialization: '  + JSON.stringify(i-1) + '</h1></body></html>';
    
    context.succeed(html);
    
//  callback(null, 'This is the Udemy Example API with external initialization: ' + JSON.stringify(i-1));
};

```

## API GW Configuration

Explained at this address. 
https://kennbrodhagen.net/2016/01/31/how-to-return-html-from-aws-api-gateway-lambda/  

### Method Response

1. Navigate to the Method Response for the API's GET method.
2. Open up the 200 under HTTP Status and add a Response Header named Content-Type. Be sure to save it with the green check mark. If you try pressing enter to save it will clear the field and not save.
3. Delete the application/json Response Model for 200

### Integration Response

1. Navigate to the Integration Response for the API's GET method.
2. Open up the 200 Response, Header Mappings, and Mapping Templates.
3. Edit the Response Header Content-Type and set the Mapping value to `'text/html'` (be sure to use single quotes). Don't forget to save it with the green checkmark icon.
4. Delete the `application/json` Content-Type under Mapping Templates.
5. Add the Content-Type `text/html` (no quotes this time).
6. Select Mapping Template in the right-hand drop-down box.
7. Set the value of Template to `$input.path('$')` and save with the green checkmark.
