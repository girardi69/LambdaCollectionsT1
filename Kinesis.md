<b>index.js</b>
```javascript
const _ = require('lodash');

const AWS = require('aws-sdk');
const kinesisClient = new AWS.Kinesis({
  'region': 'us-east-1'
});

const employeeList = require('./employee.json');

const recordsToTransmit = _.map(employeeList, attachPartitionKey);

const params = {
  Records: recordsToTransmit,
  StreamName: 'my-stream-2'
};

kinesisClient.putRecords(params, (err, data) => {
  if (err) {
    console.log(err, err.stack);
  }
  else {
    console.log(data);
  }  
});  
  
function attachPartitionKey(record) {  
  return {  
    'PartitionKey': record.id.toString(),  
    'Data': JSON.stringify(record) //new Buffer() or a string  
  };  

}  
```

<b>package.json</b>
```javascript
{
  "name": "kinesis-producer",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "aws-sdk": "^2.112.0",
    "lodash": "^4.17.4"
  }
}
```
