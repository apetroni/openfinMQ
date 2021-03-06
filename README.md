# Demo RabbitMQ / Node / Socket IO / OpenFin / Angular 

## Overview
A basic process set that integrates data flowing through a rabbitMQ server combined with a NodeJS server that subsequently makes the data available via websockets (socket I/O) 

## Getting started 

(`$ ...` indicates entries to the command line)

* [download and install RabbitMQ](http://www.rabbitmq.com/download.html)
* clone this repo `$ git clone https://github.com/openfin/openfinMQ.git`
* install dependencies `$ npm install`
* install bower dependencies:
	* cd into the client directory `$ cd client`
	* `bower install`
* start server `$ rabbitmq-server`
* start publisher (from root directory) `$ node server/publisher.js`
* start index (from root directory) `$ node server/server.js`

## Hooking up to OpenFin

To run the web client as an OpenFin application

*	Create an OpenFin app via our [generator](https://github.com/openfin/generator-openfin)
* In the OpenFin project's directory, edit the file `public/app.json` so the `url` key points to the node server (defaults to localhost:3000)
````js
{
    "startup_app": {
    		...
        "url": <Your Path Goes Here>,
				...
    },
    "runtime": {
        ...
    },
    "shortcut": {
        ...
    }
}

````

## Hooking up your own data

If you have your own data source you can hook it up to the Angular app. You would have to connect to your WebSocket and swap out the call to `socket.on(...)` in `client/scripts/controllers/main.js` to one that handles the socket you connected to. 

The structure of the json the app expects is an object that contains a `demo` key which is an array of objects structured as follows: 
````js
{
	demo: [{
		spread: "5YR/10YR",
		bps: 120,
		change: 2,
		dv01: 12,
		hedge: 3

	},
	{
		...
	}]
}
````
		
## Disclaimers
* This is an open source project and all are encouraged to contribute.
* Its possible that the repo is not actively maintained.

## Support
Please enter an issue in the repo for any questions or problems. 
<br> Alternatively, please contact us at support@openfin.co

