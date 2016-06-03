Honeywell Captuvo Plugin
============

This is a Ionic plugin to interact with Honeywell Captuvo sled for iPhones, iPod Touches and iPad Minis (https://www.honeywellaidc.com/en-US/Pages/Product.aspx?category=enterprise-sleds-for-apple-devices&cat=HSM&pid=CaptuvoSL22). The plugin works by interacting with the native SDK provided by Honeywell to handle barcode scans and magstripe reads.

NOTE 1: the SL62 has a different SDK that needs to be swapped out in this plugin

NOTE: this plugin includes version 2.13.611 of the SL42 SDK.  **You must independently agree to the EULA from HoneyWell.**

=============

To install, run the following from your project command line: 

```$ cordova plugin add https://github.com/truth86/fql-captuvo-laserscanner.git```


==============


<h3>To Use:</h3>

Register for callbacks for barcode scanning and/or magnetic stripe reads:
```
   captuvo.registerScannerCallback(function(barcode){
        console.log("Barcode scanned: " + barcode);
        //TODO: handle barcode/label type
    });
       
```


=============
<h3>More API options:</h3>

<h5>Battery Monitor</h5>
```
  captuvo.registerBatteryCallback(function(level){
    console.log("BATTERY: " + level + " of 4");
  });
```

<h5>Ready Events</h5>
Document level events will be broadcast to let you know when the hardware is ready.
```
  document.addEventListener("magstripeReady", function(){
      console.log("MSR READY");
  });
```
<h6>Events:</h6>
* `magstripeReady` - the magnetic stripe hardware is ready for swipes.  NOTE: You must register a callback to initialize the hardware.
* `scannerReady` - the barcode scanner is ready for scans.  NOTE: You must register a callback to initialize the hardware.
* `captuvoConnected` - the captuvo sled is connected and ready for use.  NOTE: this event will not fire if your app is launched after the device is already in the sled
* `captuvoDisconnected` - the captuvo sled has been disconnected


==============
Copyright 2016 Anatoly Sokolov.
