# Website uptime Event Emitter

Ping-monitor (Node-monitot) is a tool for monitoring your website's uptime. If the website is up or down an event is emitted.

# Installation
```
npm install ping-monitor
```


# How to use
```
var Monitor = require('ping-monitor');

var sitex-monitor = new Monitor(options);

sitex-monitor.on(event, callback(response) {
    // Do something with the response 
});
```


## Options

- `website` (* require) - The url of the website to be monitored
- `timeout` (defaults to 15) - interval for checking website availability in seconds.



## Emitted Events

- `up` - All is good website is up
- `down` - Not good, website is download
- `error` - Bad, request cannot load website



## response object

- `object.website` - website being monitored
- `object.time` - time in milliseconds
- `object.responseCode` - http response code
- `object.responseMessage` -  http response code message



## Example
```
var Monitor = require('ping-monitor');


var sitex-monitor = new Monitor({
    website: 'http://www.rflab.co.za',
    timeout: 10
});


sitex-monitor.on('error', function (msg) {
    console.log(msg);
});


sitex-monitor.on('up', function (res) {
    console.log('Yay!! ' + res.website + ' is up.');
});


sitex-monitor.on('down', function (res) {
    console.log('Shit!! ' + res.website + ' is down!');
});
```



