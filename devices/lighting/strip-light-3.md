# Strip Light 3

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Strip Light 3_                                                                             |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key              | Value Type | Description                                               |
| ---------------- | ---------- | --------------------------------------------------------- |
| deviceId         | String     | device ID                                                 |
| deviceType       | String     | device type. _Strip Light 3_                              |
| hubDeviceId      | String     | device's parent Hub ID                                    |
| version          | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| power            | String     | ON/OFF state                                              |
| brightness       | Integer    | the brightness value, range from 1 to 100                 |
| color            | String     | the color value, RGB "255:255:255"                        |
| colorTemperature | Integer    | the color temperature value, range from 2700 to 6500      |

---

## Control Commands

| deviceType    | commandType | Command             | command parameter           | Description           |
| ------------- | ----------- | ------------------- | --------------------------- | --------------------- |
| Strip Light 3 | command     | turnOn              | default                     | set to ON state       |
| Strip Light 3 | command     | turnOff             | default                     | set to OFF state      |
| Strip Light 3 | command     | toggle              | default                     | toggle state          |
| Strip Light 3 | command     | setBrightness       | `{0-100}`                   | set brightness        |
| Strip Light 3 | command     | setColor            | `"{0-255}:{0-255}:{0-255}"` | set RGB color value   |
| Strip Light 3 | command     | setColorTemperature | `{2700-6500}`               | set color temperature |

---

## Webhook Events

| Key Name         | Value Type | Description                                                                            |
| ---------------- | ---------- | -------------------------------------------------------------------------------------- |
| eventType        | String     | the type of events                                                                     |
| eventVersion     | String     | the current event version                                                              |
| context          | Object     | the detail info of the event                                                           |
| deviceType       | String     | the type of the device                                                                 |
| deviceMac        | String     | the MAC address of the device                                                          |
| powerState       | String     | ON/OFF state                                                                           |
| brightness       | Integer    | attributes of the context object. the brightness value, range from 1 to 100            |
| colorTemperature | Integer    | attributes of the context object. the color temperature value, range from 2700 to 6500 |
| color            | String     | the color value, in the format of RGB value, "255:255:255"                             |
| timeOfSample     | Long       | the time stamp when the event is sent                                                  |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Strip Light 3",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",//"ON"or"OFF"
        "brightness": 10,
        "color": "255:255:0",
        "colorTemperature": 3500,
        "timeOfSample": 123456789
    }
}

```
