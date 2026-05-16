# Outdoor Meter

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _WoIOSensor_                                            |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key         | Value Type | Description                                                                                                          |
| ----------- | ---------- | -------------------------------------------------------------------------------------------------------------------- |
| deviceId    | String     | device ID                                                                                                            |
| deviceType  | String     | device type. _WoIOSensor_                                                                                            |
| hubDeviceId | String     | device's parent Hub ID                                                                                               |
| battery     | Integer    | Four-segment battery level division,`<10%, shown as 10;10%~20%, shown as 20;20%~60%, shown as 60;≥60%, shown as 100` |
| version     | String     | the current firmware version, e.g. V4.2                                                                              |
| temperature | Float      | temperature in celsius                                                                                               |
| humidity    | Integer    | humidity percentage                                                                                                  |

---

## Webhook Events

| Key Name     | Value Type | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| eventType    | String     | the type of events                         |
| eventVersion | String     | the current event version                  |
| context      | Object     | the detail info of the event               |
| deviceType   | String     | the type of the device                     |
| deviceMac    | String     | the MAC address of the device              |
| temperature  | Float      | the current temperature reading            |
| scale        | String     | the current temperature unit being used    |
| humidity     | Integer    | the current humidity reading in percentage |
| battery      | Integer    | the current battery level, `0-100`         |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoIOSensor",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature": 22.5,
        "scale": "CELSIUS",
        "humidity": 31,
        "battery":100,
        "timeOfSample": 123456789
    }
}
```
