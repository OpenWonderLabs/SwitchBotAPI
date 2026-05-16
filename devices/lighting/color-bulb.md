# Color Bulb

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Color Bulb_                                                                                |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key              | Value Type | Description                                                                                              |
| ---------------- | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId         | String     | device ID                                                                                                |
| deviceType       | String     | device type. _Color Bulb_                                                                                |
| hubDeviceId      | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |
| power            | String     | ON/OFF state                                                                                             |
| brightness       | Integer    | the brightness value, range from 1 to 100                                                                |
| version          | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3                                                |
| color            | String     | the color value, RGB "255:255:255"                                                                       |
| colorTemperature | Integer    | the color temperature value, range from 2700 to 6500                                                     |

---

## Control Commands

| deviceType | commandType | Command             | command parameter           | Description           |
| ---------- | ----------- | ------------------- | --------------------------- | --------------------- |
| Color Bulb | command     | turnOn              | default                     | set to ON state       |
| Color Bulb | command     | turnOff             | default                     | set to OFF state      |
| Color Bulb | command     | toggle              | default                     | toggle state          |
| Color Bulb | command     | setBrightness       | `{1-100}`                   | set brightness        |
| Color Bulb | command     | setColor            | `"{0-255}:{0-255}:{0-255}"` | set RGB color value   |
| Color Bulb | command     | setColorTemperature | `{2700-6500}`               | set color temperature |

---

## Webhook Events

| Key Name         | Value Type | Description                                                |
| ---------------- | ---------- | ---------------------------------------------------------- |
| eventType        | String     | the type of events                                         |
| eventVersion     | String     | the current event version                                  |
| context          | Object     | the detail info of the event                               |
| deviceType       | String     | the type of the device                                     |
| deviceMac        | String     | the MAC address of the device                              |
| powerState       | String     | the current power state of the device, "ON" or "OFF"       |
| brightness       | Integer    | the brightness value, range from 1 to 100                  |
| color            | String     | the color value, in the format of RGB value, "255:255:255" |
| colorTemperature | Integer    | the color temperature value, range from 2700 to 6500       |
| timeOfSample     | Long       | the time stamp when the event is sent                      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoBulb",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "brightness": 10,
        "color":"255:245:235",
        "colorTemperature":3500,
        "timeOfSample": 123456789
    }
}
```
