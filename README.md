# mt-downloader [![Build Status](https://travis-ci.org/tusharmath/Multi-threaded-downloader.svg?branch=master)](https://travis-ci.org/tusharmath/Multi-threaded-downloader) [![npm](https://img.shields.io/npm/v/mt-downloader.svg)]() [![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/) [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release) [![js-standard-style](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)

This is a nodejs based application which help you in performing downloads via Http.


## Features
0. **Multi threaded downloads:** In a conventional single threaded download you might experience poor performance due to network lags. So you don't completely utilize your bandwidth. With multiple threads there is always one thread which is getting data thus minimizing the wait period between data packets. This doesn't mean that you will be able to download faster than what your data plan. You will only be able to use the bandwidth in a more optimized fashion.

0. **Stop and start from the last downloaded byte:**. You don't have to worry about internet getting disconnected or your computer shutting down while downloading. You can quite easily start from the last byte that was downloaded.

0. **Console application:** [mt-console](https://github.com/tusharmath/mtd-console)

	**NOTE:** the current console application depends on an older version of mt-downloader.

## Installation

The conventional npm installation process needs to be followed.

```bash
npm install mt-downloader --save-dev
```

## .mtd file
Once the download starts the library will create a file with a **.mtd** extension. This file contains some meta information related to the download and is a little bigger *(around 512 bytes)* than the original download size. The **.mtd** file can be used later to restart downloads from where the last byte that was downloaded. After the download is completed the downloader will truncate the file to remove that meta data.

## New-Downloads

```javascript
var createDownload = require('mt-downloader').createDownload
var url = 'https://upload.wikimedia.org/wikipedia/commons/4/47/Gadget_the_pug_expressive_eyes.jpg';
var file = '/Users/tusharmathur/Desktop/temp/Gadget_the_pug_expressive_eyes.jpg';
var downloader = createDownload({file, url});
downloader.start() // returns an observable
```

The `start()` method returns an observable. It can easily be converted into a promise by calling `toPromise()` method on it.

```js
downloader.start().toPromise()
```


## Re-Downloads
If you want to restart a download from where it left off. You just need to provide the path of the original file.

```javascript
//File should have NOT have .mtd extension
var file = '/Users/tusharmathur/Desktop/temp/Gadget_the_pug_expressive_eyes.jpg'
var downloader = createDownload({file})
downloader.download().toPromise()
```
