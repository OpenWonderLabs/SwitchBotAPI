# Lock Lite

---

## Device List Information

| Key                | Value Type      | Description                                                                                       |
| ------------------ | --------------- | ------------------------------------------------------------------------------------------------- |
| deviceId           | String          | device ID                                                                                         |
| deviceName         | String          | device name                                                                                       |
| deviceType         | String          | device type. _Lock Lite_                                                                          |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device                              |
| hubDeviceId        | String          | device's parent Hub ID                                                                            |
| group              | Boolean         | determines if a Lock is grouped with another Lock or not                                          |
| master             | Boolean         | determines if a Lock is the master device or not when grouped with another Lock in Dual Lock mode |
| groupName          | String          | the name of the Lock group                                                                        |
| lockDevicesIds     | Array<deviceId> | a list of Lock device IDs such that the Lock devices are being grouped in Dual Lock mode          |

---

## Device Status

| Key         | Value Type | Description                                                                          |
| ----------- | ---------- | ------------------------------------------------------------------------------------ |
| deviceId    | String     | device ID                                                                            |
| deviceType  | String     | device type. _Lock Lite_                                                             |
| hubDeviceId | String     | device's parent Hub ID                                                               |
| battery     | Integer    | the current battery level                                                            |
| version     | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3                            |
| lockState   | String     | determines if locked or not, _jammed_, _unlock_ or _lock_                            |
| calibrate   | Boolean    | determines if the open and the closed positions have been properly calibrated or not |

---

## Control Commands

| deviceType | commandType | Command | command parameter | Description                 |
| ---------- | ----------- | ------- | ----------------- | --------------------------- |
| Lock Lite  | command     | lock    | default           | rotate to locked position   |
| Lock Lite  | command     | unlock  | default           | rotate to unlocked position |

---

## Webhook Events

| Key Name     | Value Type | Description                           |
| ------------ | ---------- | ------------------------------------- |
| eventType    | String     | the type of events                    |
| eventVersion | String     | the current event version             |
| context      | Object     | the detail info of the event          |
| deviceType   | String     | the type of the device                |
| deviceMac    | String     | the MAC address of the device         |
| lockState    | String     | determines if locked or not           |
| battery      | Integer    | the battery level                     |
| timeOfSample | Long       | the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoLockLite",
        "deviceMac": DEVICE_MAC_ADDR,
        "lockState": "LOCKED",
        "battery": 90,
        "timeOfSample": 123456789
    }
}
```
