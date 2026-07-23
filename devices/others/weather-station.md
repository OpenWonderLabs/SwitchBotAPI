# Weather Station

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _WeatherStation_                                        |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key         | Value Type | Description                                     |
| ----------- | ---------- | ----------------------------------------------- |
| deviceId    | String     | device ID                                       |
| deviceType  | String     | device type. _WeatherStation_                   |
| hubDeviceId | String     | device's parent Hub ID                          |
| battery     | Integer    | the current battery level, 0-100                |
| version     | String     | the current firmware version, e.g. V6.3         |
| temperature | Float      | temperature in celsius                          |
| humidity    | Integer    | humidity percentage                             |

---

## Control Commands

| deviceType      | commandType | Command      | command parameter                            | Description                                     |
| --------------- | ----------- | ------------ | -------------------------------------------- | ----------------------------------------------- |
| Weather Station | command     | customQuote  | custom text, e.g. `"Oh sea, you have so much water!"` | Set a custom quote                    |
| Weather Station | command     | cancelCustom | default                                      | Cancel the custom quote and revert to default   |
| Weather Station | command     | customPage   | custom text, e.g. `"Oh, the ocean is so huge!"` | Set a custom page text                       |

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
        "deviceType": "WeatherStation",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature": 13,
        "humidity": 18,
        "scale": "CELSIUS",
        "battery": 100,
        "timeOfSample": 123456789
    }
}
```
