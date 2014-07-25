# winston-elasticsearch
An ElasticSearch transport for Winston.

## How to install
    npm install --save winston https://github.com/Whoaa512/winston-elasticsearch/tarball/master

## How to use
More example(s) available in the examples directory.

    var winston = require( 'winston' );
    var Elasticsearch = require( 'winston-elasticsearch' );

    var logger = new winston.Logger({
      transports: [
        new Elasticsearch({
          level: 'info',
          host: 'http://localhost:9200',
          indexName: 'logs',
          typeName: 'logs',
          requestTimeout: 30000
        })
      ]
    });

## Options
* *level* ['info'] log level
* *fireAndForget* [false] if set to true, it sends the data in back ground. If a callback is passed, it gets callback at the beginning of the function without parameters.
* *indexName* ['logs'] Elasticsearch index
* *typeName* ['log'] Elasticsearch type
* *client* An instance of [elasticsearch client](https://github.com/elasticsearch/elasticsearch-js) if given all the following options are ignored.
* *host* Ignored if `client` is set. [See elasticsearch options](https://github.com/elasticsearch/elasticsearch-js/blob/2.3/src%2Flib%2Fclient.js#L2-L24)
* *requestTimeout* Ignored if `client` is set. Defaults to 30000
  - Number of milliseconds to wait before aborting a request. Be sure to increase this if you do large bulk operations.
* *source* An identifier for the system/site/request that triggered the entry. Defaults to directory name of the main module filename of main module if not set.
  - Can be access within an overridden log function using `this.source`
* *disable_fields* Disables the automatically generated and added fields that include PID, user, memory usage, runtime, etc.
  - Can be access within an overridden log function using `this.source`
