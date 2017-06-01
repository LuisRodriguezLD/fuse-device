fuse-device
============

Use the basic Device functions such as UUID and current localization from Fuse.


## Installation

Using [fusepm](https://github.com/bolav/fusepm)

    $ fusepm install https://github.com/MaxGraey/fuse-device

Or manually copy **Device.uno** to your project and add link in .unoproj.
See example: https://github.com/MaxGraey/fuse-device/tree/master/example

### Support
- **iOS**
- **Android**
- **Preview**


### JavaScript

```js
    var Device = require('Device');

    console.log('Current device language: ' + Device.locale); // format in BCP-47 for all mobile platforms
    // output example: en-US
    
    console.log('Vendor name: '        + Device.vendor);
    console.log('Model name: '         + Device.model);
    console.log('System: '             + Device.system);
    console.log('System version: '     + Device.systemVersion);
    console.log('System SDK ver: '     + Device.SDKVersion);
    console.log('Logical processors: ' + Device.cores);
    console.log('is retina?: '         + Device.isRetina);
```

Since reading UUID in Android requires a run-time permission to `READ_PHONE_STATE`,
the UUID is not accessible as a static property on `Device`. Instead, UUID is returned
in a promise from `getUUID()` method on all target platforms.

```js
    var Device = require('Device');
    Device.getUUID().then(function(uuid) {
        console.log('UUID: ' + uuid);
        // output example:
        // UUID: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    }).catch(function(error) {
        console.log('UUID error: ' + error);
        // output example:
        // UUID error: Permissions could not be requested or granted.
    });
```
