# Strip Light

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Strip Light_                                                                               |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key          | Value Type | Description                                                                                              |
| ------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId     | String     | device ID                                                                                                |
| deviceType   | String     | device type. _Strip Light_                                                                               |
| hubDeviceId  | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |
| power        | String     | ON/OFF state                                                                                             |
| version      | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3                                                |
| brightness   | Integer    | the brightness value, range from 1 to 100                                                                |
| color        | String     | the color value, RGB "255:255:255"                                                                       |
| onlineStatus | String     | the connection status of the device. _online_ or _offline_                                               |

---

## Control Commands

| deviceType  | commandType | Command       | command parameter           | Description         |
| ----------- | ----------- | ------------- | --------------------------- | ------------------- |
| Strip Light | command     | turnOn        | default                     | set to ON state     |
| Strip Light | command     | turnOff       | default                     | set to OFF state    |
| Strip Light | command     | toggle        | default                     | toggle state        |
| Strip Light | command     | setBrightness | `{1-100}`                   | set brightness      |
| Strip Light | command     | setColor      | `"{0-255}:{0-255}:{0-255}"` | set RGB color value |

---

## Webhook Events

| Key Name     | Value Type | Description                                                |
| ------------ | ---------- | ---------------------------------------------------------- |
| eventType    | String     | the type of events                                         |
| eventVersion | String     | the current event version                                  |
| context      | Object     | the detail info of the event                               |
| deviceType   | String     | the type of the device                                     |
| deviceMac    | String     | the MAC address of the device                              |
| powerState   | String     | the current power state of the device, "ON" or "OFF"       |
| brightness   | Integer    | the brightness value, range from 1 to 100                  |
| color        | String     | the color value, in the format of RGB value, "255:255:255" |
| timeOfSample | Long       | the time stamp when the event is sent                      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoStrip",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "brightness": 10,
        "color": "255:245:235",
        "timeOfSample": 123456789
    }
}
```
