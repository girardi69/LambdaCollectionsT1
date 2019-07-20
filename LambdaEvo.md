'''javascript

let i = 1;

exports.fi = function(event, context, callback) {

    console.log(i++);
    
  

    var html = '<html><head><title>HTML from API Gateway/Lambda</title></head>' + 
        '<body><h1>This is the Udemy Example API with external initialization: '  + JSON.stringify(i-1) + '</h1></body></html>';
    
    context.succeed(html);
    
//  callback(null, 'This is the Udemy Example API with external initialization: ' + JSON.stringify(i-1));
};

''''
