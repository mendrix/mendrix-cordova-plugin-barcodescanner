BarcodeScanner
==============

[![Build Status](https://travis-ci.org/hypery2k/cordova-barcodescanner-plugin.svg?branch=master)](https://travis-ci.org/hypery2k/cordova-barcodescanner-plugin) [![Build status](https://ci.appveyor.com/api/projects/status/298mrueury1ntrf4?svg=true)](https://ci.appveyor.com/project/hypery2k/cordova-barcodescanner-plugin)
 [![Bountysource](https://www.bountysource.com/badge/tracker?tracker_id=12908089)](https://www.bountysource.com/trackers/12908089-hypery2k-cordova-barcodescanner-plugin?utm_source=12908089&utm_medium=shield&utm_campaign=TRACKER_BADGE)

> cross-platform barcode scanner for cordova

## Supported Platforms

- Android
- iOS
- Windows 8
- Windows Phone 8


## Installation

```
cordova plugin add cordova-plugin-barcodescanner
```

## Development

### Running integration tests

execute the `runIntegrationTests.sh` script for a specific platform:

```
PLATFORM='android' ./runIntegrationTests.sh
```

```
PLATFORM='ios' ./runIntegrationTests.sh
```

### Details


>The Android source for this project includes an Android Library Project.
plugman currently doesn't support Library Project refs, so its been
prebuilt as a jar library. Any updates to the Library Project should be
committed with an updated jar.

## Using the plugin ##
The plugin creates the object `cordova/plugin/BarcodeScanner` with the method `scan(success, fail)`. 

The following barcode types are currently supported:
### Android

* QR_CODE
* DATA_MATRIX
* UPC_E
* UPC_A
* EAN_8
* EAN_13
* CODE_128
* CODE_39
* CODE_93
* CODABAR
* ITF
* RSS14
* PDF417
* RSS_EXPANDED

### iOS

* QR_CODE
* DATA_MATRIX
* UPC_E
* UPC_A
* EAN_8
* EAN_13
* CODE_128
* CODE_39
* ITF

### Windows8

* UPC_A
* UPC_E
* EAN_8
* EAN_13
* CODE_39
* CODE_93
* CODE_128
* ITF
* CODABAR
* MSI
* RSS14
* QR_CODE
* DATA_MATRIX
* AZTEC
* PDF417

### Windows Phone 8

* UPC_A
* UPC_E
* EAN_8
* EAN_13
* CODE_39
* CODE_93
* CODE_128
* ITF
* CODABAR
* MSI
* RSS14
* QR_CODE
* DATA_MATRIX
* AZTEC
* PDF417

`success` and `fail` are callback functions. Success is passed an object with data, type and cancelled properties. Data is the text representation of the barcode data, type is the type of barcode detected and cancelled is whether or not the user cancelled the scan.

A full example could be:
```
   cordova.plugins.barcodeScanner.scan(
      function (result) {
          alert("We got a barcode\n" +
                "Result: " + result.text + "\n" +
                "Format: " + result.format + "\n" +
                "Cancelled: " + result.cancelled);
      }, 
      function (error) {
          alert("Scanning failed: " + error);
      }
   );
```

## Encoding a Barcode ##
The plugin creates the object `window.plugins.barcodeScanner` with the method `encode(type, data, success, fail)`.
Supported encoding types:

* TEXT_TYPE
* EMAIL_TYPE
* PHONE_TYPE
* SMS_TYPE

```
A full example could be:

   cordova.plugins.barcodeScanner.encode(BarcodeScanner.Encode.TEXT_TYPE, "http://www.nytimes.com", function(success) {
            alert("encode success: " + success);
          }, function(fail) {
            alert("encoding failed: " + fail);
          }
        );
```

## Windows8 quirks ##
Windows 8 implenemtation currently doesn't support encode functionality.

## Windows Phone 8 quirks ##
Windows Phone 8 implenemtation currently doesn't support encode functionality.


## Licence ##

The MIT License

Copyright (c) 2010 Matt Kane

Copyright (c) 2015 Martin Reinhardt

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
