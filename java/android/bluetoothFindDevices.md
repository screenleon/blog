# Bluetooth Find Devices
================================

**Author**: Lien Chen  **Date**: 2021-11-10

* When I use BluetoothAdapter.startDiscovery, I can not find device by BroadcastReceiver's BluetoothDevice.ACTION_FOUND.
* When I use BluetoothLeScanner.startScan, also I can not find device by ScanCallback onScanResult.
* Finally I saw the error which said that "java.lang.SecurityException: Need ACCESS_COARSE_LOCATION or ACCESS_FINE_LOCATION permission to get scan results"

* Add below code to fix this problem

AndroidManifest.xml
```xml
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```

```java
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.M) {
        // private static int PERMISSION_REQUEST_COARSE_LOCATION = 456
        // User Custom request code
        requestPermissions(new String[]{Manifest.permission.ACCESS_COARSE_LOCATION}, Permission.PERMISSION_REQUEST_COARSE_LOCATION);
    }
```
