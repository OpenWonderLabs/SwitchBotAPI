# Meter Pro CO2

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _MeterPro(CO2)_                                         |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key         | Value Type | Description                             |
| ----------- | ---------- | --------------------------------------- |
| deviceId    | String     | device ID                               |
| deviceType  | String     | device type. _MeterPro(CO2)_            |
| hubDeviceId | String     | device's parent Hub ID                  |
| battery     | Integer    | the current battery level, 0-100        |
| version     | String     | the current firmware version, e.g. V4.2 |
| temperature | Float      | temperature in celsius                  |
| humidity    | Integer    | humidity percentage                     |
| CO2         | Integer    | CO2 ppm value, 0-9999                   |

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
| CO2          | Integer    | CO2 ppm value, 0-9999                      |
| battery      | Integer    | the current battery level, `0-100`         |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "MeterPro(CO2)",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature": 22.5,
        "scale": "CELSIUS",
        "humidity": 31,
        "CO2": 1203,
        "battery":100,
        "timeOfSample": 123456789
    }
}
```
