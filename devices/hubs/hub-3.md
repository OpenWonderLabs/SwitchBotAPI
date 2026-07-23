# Hub 3

---

## Device Status

| Key          | Value Type | Description                                                |
| ------------ | ---------- | ---------------------------------------------------------- |
| deviceId     | String     | device ID                                                  |
| deviceType   | String     | device type. _Hub 3_                                       |
| hubDeviceId  | String     | Hub ID, equivalent to device ID                            |
| version      | String     | the current firmware version, e.g. V4.2                    |
| temperature  | Float      | temperature in celsius                                     |
| lightLevel   | Integer    | the level of illuminance of the ambience light, 1~10       |
| humidity     | Integer    | humidity percentage                                        |
| moveDetected | Boolean    | determines if motion is detected                           |
| onlineStatus | String     | the connection status of the device. _online_ or _offline_ |

---

## Webhook Events

| Key Name       | Value Type | Description                                                                                                                                    |
| -------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| eventType      | String     | the type of events                                                                                                                             |
| eventVersion   | String     | the current event version                                                                                                                      |
| context        | Object     | the detail info of the event                                                                                                                   |
| detectionState | String     | the motion state of the device, "DETECTED" stands for motion is detected; "NOT_DETECTED" stands for motion has not been detected for some time |
| deviceMac      | String     | attributes of the context object. the MAC address of the device                                                                                |
| deviceType     | String     | attributes of the context object. the type of the device                                                                                       |
| humidity       | Integer    | the current humidity reading in percentage                                                                                                     |
| lightLevel     | Integer    | the level of illuminance of the ambience light, 1~10                                                                                           |
| scale          | String     | the current temperature unit being used                                                                                                        |
| temperature    | Float      | the current temperature reading                                                                                                                |
| timeOfSample   | Long       | attributes of the context object. the time stamp when the event is sent                                                                        |

```js
{
  "eventType": "changeReport",
  "eventVersion": "1",
  "context": {
    "detectionState": "DETECTED",
    "deviceMac": "B0E9FE582974",
    "deviceType": "Hub 3",
    "humidity": 45,
    "lightLevel": 10,
    "scale": "CELSIUS",
    "temperature": 30.3,
    "timeOfSample": 1742807095763
  }
}
```
