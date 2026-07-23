# RGBIC Neon Wire Rope Light

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _RGBIC Neon Wire Rope Light_                                                                |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key          | Value Type | Description                                                                                              |
| ------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId     | String     | device ID                                                                                                |
| deviceType   | String     | device type. _RGBIC Neon Wire Rope Light_                                                                |
| hubDeviceId  | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |
| version      | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3                                                |
| power        | String     | ON/OFF state                                                                                             |
| onlineStatus | String     | the connection status of the device. _online_ or _offline_                                               |
| brightness   | Integer    | the brightness value, range from 1 to 100                                                                |
| color        | String     | the color value, RGB "255:255:255"                                                                       |

---

## Control Commands

| deviceType                 | commandType | Command       | command parameter           | Description         |
| -------------------------- | ----------- | ------------- | --------------------------- | ------------------- |
| RGBIC Neon Wire Rope Light | command     | turnOn        | default                     | set to ON state     |
| RGBIC Neon Wire Rope Light | command     | turnOff       | default                     | set to OFF state    |
| RGBIC Neon Wire Rope Light | command     | toggle        | default                     | toggle state        |
| RGBIC Neon Wire Rope Light | command     | setBrightness | `{0-100}`                   | set brightness      |
| RGBIC Neon Wire Rope Light | command     | setColor      | `"{0-255}:{0-255}:{0-255}"` | set RGB color value |

---

## Webhook Events

| Key Name     | Value Type | Description                                                                 |
| ------------ | ---------- | --------------------------------------------------------------------------- |
| eventType    | String     | the type of events                                                          |
| eventVersion | String     | the current event version                                                   |
| context      | Object     | the detail info of the event                                                |
| deviceType   | String     | attributes of the context object. the type of the device                    |
| deviceMac    | String     | attributes of the context object. the MAC address of the device             |
| powerState   | String     | attributes of the context object. ON/OFF state                              |
| brightness   | Integer    | attributes of the context object. the brightness value, range from 1 to 100 |
| color        | String     | the color value, in the format of RGB value, "255:255:255"                  |
| timeOfSample | Long       | attributes of the context object. the time stamp when the event is sent     |

```js
{
   "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "RGBICWW Strip Light",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",//"ON"or"OFF"
        "brightness": 10,
        "color": "255:255:0",
        "timeOfSample": 123456789
    }
}
```
