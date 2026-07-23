# Ceiling Light Pro

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Ceiling Light Pro_                                                                         |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key              | Value Type | Description                                                                                              |
| ---------------- | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId         | String     | device ID                                                                                                |
| deviceType       | String     | device type. _Ceiling Light Pro_                                                                         |
| hubDeviceId      | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |
| version          | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3                                                |
| power            | String     | ON/OFF state                                                                                             |
| brightness       | Integer    | the brightness value, range from 1 to 100                                                                |
| colorTemperature | Integer    | the color temperature value, range from 2700 to 6500                                                     |
| onlineStatus     | String     | the connection status of the device. _online_ or _offline_                                               |

---

## Control Commands

| deviceType        | commandType | Command             | command parameter | Description               |
| ----------------- | ----------- | ------------------- | ----------------- | ------------------------- |
| Ceiling Light Pro | command     | turnOn              | default           | set to ON state           |
| Ceiling Light Pro | command     | turnOff             | default           | set to OFF state          |
| Ceiling Light Pro | command     | toggle              | default           | toggle state              |
| Ceiling Light Pro | command     | setBrightness       | `{1-100}`         | set brightness            |
| Ceiling Light Pro | command     | setColorTemperature | `{2700-6500}`     | set the color temperature |

---

## Webhook Events

| Key Name         | Value Type | Description                                                                            |
| ---------------- | ---------- | -------------------------------------------------------------------------------------- |
| eventType        | String     | the type of events                                                                     |
| eventVersion     | String     | the current event version                                                              |
| context          | Object     | the detail info of the event                                                           |
| deviceType       | String     | attributes of the context object. the type of the device                               |
| deviceMac        | String     | attributes of the context object. the MAC address of the device                        |
| powerState       | String     | attributes of the context object. ON/OFF state                                         |
| brightness       | Integer    | attributes of the context object. the brightness value, range from 1 to 100            |
| colorTemperature | Integer    | attributes of the context object. the color temperature value, range from 2700 to 6500 |
| timeOfSample     | Long       | attributes of the context object. the time stamp when the event is sent                |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoCeilingPro",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "brightness": 10,
        "colorTemperature": 3500,
        "timeOfSample": 123456789
    }
}
```
