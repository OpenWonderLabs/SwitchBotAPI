# Roller Shade

---

## Device List Information

| Key                | Value Type      | Description                                                                                                              |
| ------------------ | --------------- | ------------------------------------------------------------------------------------------------------------------------ |
| deviceId           | String          | device ID                                                                                                                |
| deviceName         | String          | device name                                                                                                              |
| deviceType         | String          | device type. _Roller Shade_                                                                                              |
| bleVersion         | Integer         | firmware version                                                                                                         |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device                                                     |
| hubDeviceId        | String          | device's parent Hub ID                                                                                                   |
| groupingDevicesIds | Array<deviceId> | a list of device IDs such that the Roller Shade devices are being paired or grouped                                      |
| group              | Boolean         | determines if a device is paired with or grouped with one or more devices of the same type or not                        |
| master             | Boolean         | determines if a device is the master device or not when paired with or grouped with one or more devices of the same type |
| groupName          | String          | the name of the device group                                                                                             |

---

## Device Status

| Key           | Value Type | Description                                                                          |
| ------------- | ---------- | ------------------------------------------------------------------------------------ |
| deviceId      | String     | device ID                                                                            |
| deviceType    | String     | device type. _Roller Shade_                                                          |
| hubDeviceId   | String     | device's parent Hub ID                                                               |
| version       | String     | the current firmware version, e.g. V4.2                                              |
| calibrate     | Boolean    | determines if the open and the closed positions have been properly calibrated or not |
| battery       | Integer    | the current battery level `0-100`                                                    |
| moving        | Boolean    | determines if the device is moving or not                                            |
| slidePosition | Integer    | the current position, `0-100`                                                        |

---

## Control Commands

| deviceType   | commandType | Command     | command parameter | Description              |
| ------------ | ----------- | ----------- | ----------------- | ------------------------ |
| Roller Shade | command     | setPosition | `0~100`           | `0`, open; `100`, closed |

---

## Webhook Events

| Key Name      | Value Type | Description                                                                                                           |
| ------------- | ---------- | --------------------------------------------------------------------------------------------------------------------- |
| eventType     | String     | the type of events                                                                                                    |
| eventVersion  | String     | the current event version                                                                                             |
| context       | Object     | the detail info of the event                                                                                          |
| deviceType    | String     | the type of the device                                                                                                |
| deviceMac     | String     | the MAC address of the device                                                                                         |
| calibrate     | Boolean    | determines if the open position and the close position of a device have been properly calibrated or not               |
| slidePosition | Integer    | the percentage of the distance between the calibrated open position and closed position that the device has traversed |
| battery       | Integer    | the battery level                                                                                                     |
| timeOfSample  | Long       | the time stamp when the event is sent                                                                                 |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoRollerShade",
        "deviceMac": DEVICE_MAC_ADDR,
        "calibrate":false,
        "slidePosition":50, //0~100
        "battery":100,
        "timeOfSample": 123456789
    }
}
```
