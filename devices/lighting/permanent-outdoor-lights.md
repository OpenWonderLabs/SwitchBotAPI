# Permanent Outdoor Lights

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Permanent Outdoor Lights_                              |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key              | Value Type | Description                                                |
| ---------------- | ---------- | ---------------------------------------------------------- |
| deviceId         | String     | device ID                                                  |
| deviceType       | String     | device type. _Permanent Outdoor Lights_                    |
| hubDeviceId      | String     | device's parent Hub ID                                     |
| version          | String     | the current Wi-Fi firmware version, e.g. V3.1              |
| power            | String     | ON/OFF state                                               |
| onlineStatus     | String     | the connection status. _online_ or _offline_               |
| brightness       | Integer    | the brightness value, range from 0 to 100                  |
| color            | String     | the color value, RGB `"255:255:255"`                       |
| colorTemperature | Integer    | the color temperature value, range from 2700 to 6500       |

---

## Control Commands

| deviceType              | commandType | Command             | command parameter           | Description           |
| ----------------------- | ----------- | ------------------- | --------------------------- | --------------------- |
| Permanent Outdoor Lights | command    | turnOn              | default                     | set to ON state       |
| Permanent Outdoor Lights | command    | turnOff             | default                     | set to OFF state      |
| Permanent Outdoor Lights | command    | toggle              | default                     | toggle state          |
| Permanent Outdoor Lights | command    | setBrightness       | `{0-100}`                   | set brightness        |
| Permanent Outdoor Lights | command    | setColorTemperature | `{2700-6500}`               | set color temperature |
| Permanent Outdoor Lights | command    | setColor            | `"{0-255}:{0-255}:{0-255}"` | set RGB color value   |

---

## Webhook Events

| Key Name         | Value Type | Description                           |
| ---------------- | ---------- | ------------------------------------- |
| eventType        | String     | the type of events                    |
| eventVersion     | String     | the current event version             |
| context          | Object     | the detail info of the event          |
| deviceType       | String     | the type of the device                |
| deviceMac        | String     | the MAC address of the device         |
| powerState       | String     | ON/OFF state                          |
| brightness       | Integer    | the brightness value                  |
| color            | String     | the color value, RGB `"255:255:255"`  |
| colorTemperature | Integer    | the color temperature value           |
| timeOfSample     | Long       | the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Permanent Outdoor Lights",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "brightness": 10,
        "color": "255:255:0",
        "colorTemperature": 3500,
        "timeOfSample": 123456789
    }
}
```
