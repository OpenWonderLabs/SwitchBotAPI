# Plug Mini (EU)

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Plug Mini (EU)_                                                                            |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key             | Value Type | Description                                               |
| --------------- | ---------- | --------------------------------------------------------- |
| deviceId        | String     | device ID                                                 |
| deviceType      | String     | device type. _Plug Mini (EU)_                             |
| switchStatus    | Integer    | the current switch state. `0`, off; `1`, on               |
| voltage         | Float      | the voltage of the device, measured in Volt               |
| power           | Float      | the current power, measured in Watts                      |
| electricCurrent | Float      | the current of the device at the moment, measured in mA   |
| usedElectricity | Integer    | daily power consumption, measured in watt-minutes         |
| version         | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |

---

## Control Commands

| deviceType     | commandType | Command | command parameter | Description      |
| -------------- | ----------- | ------- | ----------------- | ---------------- |
| Plug Mini (EU) | command     | turnOn  | default           | set to ON state  |
| Plug Mini (EU) | command     | turnOff | default           | set to OFF state |
| Plug Mini (EU) | command     | toggle  | default           | toggle state     |

---

## Webhook Events

| Key Name        | Value Type | Description                                                             |
| --------------- | ---------- | ----------------------------------------------------------------------- |
| eventType       | String     | the type of events                                                      |
| eventVersion    | String     | the current event version                                               |
| context         | Object     | the detail info of the event                                            |
| deviceType      | String     | the type of the device                                                  |
| deviceMac       | String     | the MAC address of the device                                           |
| online          | Boolean    | determines if the device is connected to the internet or disconnected   |
| overTemperature | Boolean    | determines if the working temperature is over 100 degree celcius or not |
| overload        | Boolean    | determines if the device is power overloaded or not                     |
| switchStatus    | Integer    | the switch state of the device. `1`, on; `0`, off                       |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Plug Mini (EU)",
        "deviceMac": "94A990502B72",
        "online": false,
        "overTemperature": true,
        "overload": true,
        "switchStatus": 1
    }
}
```
