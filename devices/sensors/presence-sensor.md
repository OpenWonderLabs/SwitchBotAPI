# Presence Sensor

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Presence Sensor_                                       |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key         | Value Type | Description                                                                                                          |
| ----------- | ---------- | -------------------------------------------------------------------------------------------------------------------- |
| deviceId    | String     | device ID                                                                                                            |
| deviceType  | String     | device type. _Presence Sensor_                                                                                       |
| hubDeviceId | String     | device's parent Hub ID                                                                                               |
| battery     | Integer    | Four-segment battery level division,`<10%, shown as 10;10%~20%, shown as 20;20%~60%, shown as 60;≥60%, shown as 100` |
| version     | String     | the current firmware version, e.g. V4.2                                                                              |
| lightLevel  | Integer    | the level of illuminance of the ambience light, 1~20                                                                 |
| Detected    | Boolean    | determines if human is detected                                                                                      |

---

## Webhook Events

| Key Name       | Value Type | Description                                                                                                                                    |
| -------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| eventType      | String     | the type of events                                                                                                                             |
| eventVersion   | String     | the current event version                                                                                                                      |
| context        | Object     | the detail info of the event                                                                                                                   |
| deviceType     | String     | the type of the device                                                                                                                         |
| deviceMac      | String     | the MAC address of the device                                                                                                                  |
| detectionState | String     | the motion state of the device, "DETECTED" stands for motion is detected; "NOT_DETECTED" stands for motion has not been detected for some time |
| battery        | Integer    | the current battery level, `0-100`                                                                                                             |
| lightLevel     | Integer    | the level of illuminance of the ambience light, 1~20                                                                                           |
| timeOfSample   | Long       | the time stamp when the event is sent                                                                                                          |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoContact",
        "deviceMac": DEVICE_MAC_ADDR,
        "detectionState": "NOT_DETECTED",
        "battery":100,
        "lightLevel": 19,
        "timeOfSample": 123456789
    }
}
```
