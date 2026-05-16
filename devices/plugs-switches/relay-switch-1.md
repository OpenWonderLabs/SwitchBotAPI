# Relay Switch 1

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Relay Switch 1_                                                                            |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key          | Value Type | Description                                               |
| ------------ | ---------- | --------------------------------------------------------- |
| deviceId     | String     | device ID                                                 |
| deviceType   | String     | device type. _Relay Switch 1_                             |
| switchStatus | Integer    | the current switch state. `0`, off; `1`, on               |
| version      | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| hubDeviceId  | String     | Hub ID, equivalent to device ID                           |

---

## Control Commands

| deviceType     | commandType | Command | command parameter | Description                                                                                                         |
| -------------- | ----------- | ------- | ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| Relay Switch 1 | command     | turnOn  | default           | set to ON state                                                                                                     |
| Relay Switch 1 | command     | turnOff | default           | set to OFF state                                                                                                    |
| Relay Switch 1 | command     | toggle  | default           | toggle state                                                                                                        |
| Relay Switch 1 | command     | setMode | `0~3`             | set the switch mode. `0`, toggle mode; `1`, edge switch mode; `2`, detached switch mode; `3`, momentary switch mode |

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
| switchStatus    | Integer    | the switch state of the device. `1`, on; `0`, off                       |
| overTemperature | Boolean    | determines if the working temperature is over 100 degree celcius or not |
| timeOfSample    | Long       | the time stamp when the event is sent                                   |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Relay Switch 1",
        "deviceMac": DEVICE_MAC_ADDR,
        "online": false,
        "overTemperature": true,
        "switchStatus": 1,
        "timeOfSample": 123456789
    }
}
```
