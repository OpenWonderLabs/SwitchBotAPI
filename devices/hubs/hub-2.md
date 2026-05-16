# Hub 2

---

## Device Status

| Key         | Value Type | Description                                          |
| ----------- | ---------- | ---------------------------------------------------- |
| deviceId    | String     | device ID                                            |
| deviceType  | String     | device type. _Hub 2_                                 |
| hubDeviceId | String     | Hub ID, equivalent to device ID                      |
| temperature | Float      | temperature in celsius                               |
| lightLevel  | Integer    | the level of illuminance of the ambience light, 1~20 |
| version     | String     | the current firmware version, e.g. V4.2              |
| humidity    | Integer    | humidity percentage                                  |

---

## Webhook Events

| Key Name     | Value Type | Description                                                             |
| ------------ | ---------- | ----------------------------------------------------------------------- |
| eventType    | String     | the type of events                                                      |
| eventVersion | String     | the current event version                                               |
| context      | Object     | the detail info of the event                                            |
| deviceType   | String     | attributes of the context object. the type of the device                |
| deviceMac    | String     | attributes of the context object. the MAC address of the device         |
| temperature  | Float      | the current temperature reading                                         |
| humidity     | Integer    | the current humidity reading in percentage                              |
| lightLevel   | Integer    | the level of illuminance of the ambience light, 1~20                    |
| scale        | String     | the current temperature unit being used                                 |
| timeOfSample | Long       | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoHub2",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature":13,
        "humidity":18,
        "lightLevel": 19,
        "scale": "CELSIUS",
        "timeOfSample": 123456789
    }
}
```
