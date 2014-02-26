# iostreams-s3

Bootstrap stream provider for [iostreams](https://github.com/webcast-io/iostreams)

[![Build Status](https://travis-ci.org/webcast-io/iostreams-s3.png)](https://travis-ci.org/webcast-io/iostreams-s3?branch=master)
[![Coverage Status](https://coveralls.io/repos/webcast-io/iostreams-s3/badge.png?branch=master)](https://coveralls.io/r/webcast-io/iostreams-s3?branch=master)
[![Dependency Status](https://david-dm.org/webcast-io/iostreams-s3.png?theme=shields.io)](https://david-dm.org/webcast-io/iostreams-s3)

## Install

    $ npm install iostreams iostreams-s3

## Usage

```js
var iostreams = require('iostreams');

iostreams.use(require('iostreams-s3'));

// Getting an input stream
iostreams.getInputStream({
  protocol: 's3:',
  key: process.env.S3_KEY,
  secret: process.env.S3_SECRET,
  bucket: process.env.S3_BUCKET,
  region: 'eu-west-1'
  path: '/non-existent-file.png'
}, function(err, inputStream) {

});

// Getting an output stream
iostreams.getOutputStream({
  protocol: 's3:',
  key: process.env.S3_KEY,
  secret: process.env.S3_SECRET,
  bucket: process.env.S3_BUCKET,
  region: 'eu-west-1'
  path: '/file-to-be-created.flv',
  'Content-Length': fileSize, // Content-Type MUST be defined
  'Content-Type':   'video/flv',
  'x-amz-acl':      'public-read'
} function(err, outputStream) {

});

// Getting an input and output stream
iostrams.getInputAndOutputStream(
  inputConfigObject,
  outputConfigObject,
  function(err, inputStream, outputStream) {
    intputStream.pipe(outputStream);
  }
);
```

## Licence

MIT