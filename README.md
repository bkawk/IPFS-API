# Image to IPFS

A minimal API for saving and retrieving image data to/from IPFS


## Node & IPFS

First, make sure you have NPM (packaged with [Node.js](https://nodejs.org)) installed. Run `npm install` to install your element's dependencies, then run `polymer serve` to serve your element locally. Also, ensure you IPFS installed and the daemon running [IPFS](https://ipfs.io/docs/install/)

## Start the server 

```
$ npm run now
```

## Saving data to IPFS

Currently, there are no size or domain restrictions, text-based data can be stored on IPFS by making a POST request to 

```
/ipfs 
```

the body should contain an object with the key of 'data' and the value containing URI Encoded base 64 value you want to save, in this example we are storing a 1px transparent gif as a base 64 string.

```
{"data":"data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw=="}
```

the response is an object with success and hash keys

```
{
    "success": true,
    "hash": "QmczMXpyKH2msqMEYC9dD9YcvPAAkeB4GUBNxcue52rCVH"
}
```

## Getting data from IPFS

To get data from IPFS you can make a GET request containing the IPFS Hash you wish to get

```
/ipfs/QmczMXpyKH2msqMEYC9dD9YcvPAAkeB4GUBNxcue52rCVH
```

The response is an object with success and data keys

```
{
    "success": true,
    "data": "data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw=="
}
```

## Getting Image SRC Data 

Getting image src data is possible to allow direct loading of images

```
/img/QmczMXpyKH2msqMEYC9dD9YcvPAAkeB4GUBNxcue52rCVH
```

The response is just the data, no object is returned.

```
data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==
```

