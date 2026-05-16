# Candle Warmer Lamp

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Candle Warmer Lamp_                                                                        |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key          | Value Type | Description                                                |
| ------------ | ---------- | ---------------------------------------------------------- |
| deviceId     | String     | device ID                                                  |
| deviceType   | String     | device type. _Candle Warmer Lamp_                          |
| hubDeviceId  | String     | device's parent Hub ID                                     |
| onlineStatus | String     | the connection status of the device. _online_ or _offline_ |
| brightness   | Integer    | the brightness value, range from 1 to 100                  |
| version      | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3  |
| power        | String     | ON/OFF state                                               |

---

## Control Commands

| deviceType         | commandType | Command       | command parameter | Description      |
| ------------------ | ----------- | ------------- | ----------------- | ---------------- |
| Candle Warmer Lamp | command     | turnOn        | default           | set to ON state  |
| Candle Warmer Lamp | command     | turnOff       | default           | set to OFF state |
| Candle Warmer Lamp | command     | toggle        | default           | toggle state     |
| Candle Warmer Lamp | command     | setBrightness | `{0-100}`         | set brightness   |

---

## Webhook Events

| Key Name     | Value Type | Description                                                                 |
| ------------ | ---------- | --------------------------------------------------------------------------- |
| eventType    | String     | the type of events                                                          |
| eventVersion | String     | the current event version                                                   |
| context      | Object     | the detail info of the event                                                |
| deviceType   | String     | the type of the device                                                      |
| deviceMac    | String     | the MAC address of the device                                               |
| powerState   | String     | ON/OFF state                                                                |
| brightness   | Integer    | attributes of the context object. the brightness value, range from 1 to 100 |
| timeOfSample | Long       | the time stamp when the event is sent                                       |

```js
{
  "eventType": "changeReport",
  "eventVersion": "1",
  "context": {
    "brightness": 100,
    "deviceMac": "3C842777C07E",
    "deviceType": "Candle Warmer Lamp",
    "powerState": "ON",
    "timeOfSample": 1759136920594
  }
}
```
