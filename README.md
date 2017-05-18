flow-find
=========

Transform stream which filters stream data according to user-defined conditions.


## Installation

``` bash
$ npm install flow-find
```


## Examples

``` javascript
var eventStream = require( 'event-stream' ),
	fStream = require( 'flow-find' );

// Create some data...
var data = new Array( 1000 );
for ( var i = 0; i < data.length; i++ ) {
	data[ i ] = Math.random() * 100;
}

// Create a readable stream:
var readStream = eventStream.readArray( data );

// Create a new find stream:
var stream = fStream()
	.filter( function ( d ) {
		return ( d >= 95 );
	})
	.stream();

// Create the pipeline:
readStream.pipe( stream )
	.pipe( eventStream.map( function( d, clbk ) {
		clbk( null, d.toString() );
	}) )
	.pipe( process.stdout );
```

## Tests

Unit tests use the [Mocha](http://mochajs.org/) test framework with [Chai](http://chaijs.com) assertions.

Assuming you have installed Mocha, execute the following command in the top-level application directory to run the tests:

``` bash
$ mocha
```

All new feature development should have corresponding unit tests to validate correct functionality.


## License

[MIT license](http://opensource.org/licenses/MIT). 


---
## Copyright

Copyright &copy; 2014. Athan Reines.

