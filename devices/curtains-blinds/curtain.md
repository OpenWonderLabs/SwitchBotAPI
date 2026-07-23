# Curtain

---

## Device List Information

| Key                | Value Type      | Description                                                                                             |
| ------------------ | --------------- | ------------------------------------------------------------------------------------------------------- |
| deviceId           | String          | device ID                                                                                               |
| deviceName         | String          | device name                                                                                             |
| deviceType         | String          | device type. _Curtain_                                                                                  |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device                                    |
| hubDeviceId        | String          | device's parent Hub ID                                                                                  |
| curtainDevicesIds  | Array<deviceId> | a list of Curtain device IDs such that the Curtain devices are being paired or grouped                  |
| calibrate          | Boolean         | determines if the open position and the close position of a device have been properly calibrated or not |
| group              | Boolean         | determines if a Curtain is paired with or grouped with another Curtain or not                           |
| master             | Boolean         | determines if a Curtain is the master device or not when paired with or grouped with another Curtain    |
| openDirection      | String          | the opening direction of a Curtain                                                                      |

---

## Device Status

| Key           | Value Type | Description                                                                                                        |
| ------------- | ---------- | ------------------------------------------------------------------------------------------------------------------ |
| deviceId      | String     | device ID                                                                                                          |
| deviceType    | String     | device type. _Curtain_                                                                                             |
| hubDeviceId   | String     | device's parent Hub ID                                                                                             |
| calibrate     | Boolean    | determines if the open position and the close position of a device have been properly calibrated or not            |
| group         | Boolean    | determines if a Curtain is paired with or grouped with another Curtain or not                                      |
| moving        | Boolean    | determines if a Curtain is moving or not                                                                           |
| battery       | Integer    | Four-segment battery level division,`<10%, shown as 5;10%~20%, shown as 15;20%~60%, shown as 40;≥60%, shown as 80` |
| version       | String     | the current firmware version, e.g. V4.2                                                                            |
| slidePosition | String     | the percentage of the distance between the calibrated open position and closed position that Curtain has traversed |

---

## Control Commands

| deviceType | commandType | Command     | command parameter                          | Description                                                                                                           |
| ---------- | ----------- | ----------- | ------------------------------------------ | --------------------------------------------------------------------------------------------------------------------- |
| Curtain    | command     | setPosition | index0,mode0,position0<br />e.g. `0,ff,80` | mode: 0 (Performance Mode), 1 (Silent Mode), ff (default mode) <br />position: 0~100 (0 means open, 100 means closed) |
| Curtain    | command     | turnOff     | default                                    | equivalent to set position to 100                                                                                     |
| Curtain    | command     | turnOn      | default                                    | equivalent to set position to 0                                                                                       |
| Curtain    | command     | pause       | default                                    | set to PAUSE state                                                                                                    |

---

## Webhook Events

| Key Name      | Value Type | Description                                                                                                        |
| ------------- | ---------- | ------------------------------------------------------------------------------------------------------------------ |
| eventType     | String     | the type of events                                                                                                 |
| eventVersion  | String     | the current event version                                                                                          |
| context       | Object     | the detail info of the event                                                                                       |
| deviceType    | String     | the type of the device                                                                                             |
| deviceMac     | String     | the MAC address of the device                                                                                      |
| calibrate     | Boolean    | determines if the open position and the close position of a device have been properly calibrated or not            |
| group         | Boolean    | determines if a Curtain is paired with or grouped with another Curtain or not                                      |
| slidePosition | Integer    | the percentage of the distance between the calibrated open position and closed position that Curtain has traversed |
| battery       | Integer    | the battery level of a Curtain                                                                                     |
| timeOfSample  | Long       | the time stamp when the event is sent                                                                              |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoCurtain",
        "deviceMac": DEVICE_MAC_ADDR,
        "calibrate":false,
        "group":false,
        "slidePosition":50, //0~100
        "battery":100,
        "timeOfSample": 123456789
    }
}
```
