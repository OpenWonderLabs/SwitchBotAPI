# Relay Switch 2PM

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Relay Switch 2PM_                                                                          |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key                    | Value Type | Description                                                                          |
| ---------------------- | ---------- | ------------------------------------------------------------------------------------ |
| deviceId               | String     | device ID                                                                            |
| deviceType             | String     | device type. _Relay Switch 2PM_                                                      |
| online                 | Boolean    | the connection status of the device. _true_ or _false_                               |
| switch1Status          | Integer    | the current switch1 state. `0`, off; `1`, on                                         |
| switch2Status          | Integer    | the current switch2 state. `0`, off; `1`, on                                         |
| switch1Voltage         | Float      | the switch1 current voltage, measured in Volt                                        |
| switch2Voltage         | Float      | the switch2 current voltage, measured in Volt                                        |
| version                | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3                            |
| switch1Power           | Float      | the switch1 current power, measured in Watts                                         |
| switch2Power           | Float      | the switch2 current power, measured in Watts                                         |
| switch1UsedElectricity | Integer    | switch1 daily power consumption, measured in watt-minutes                            |
| switch2UsedElectricity | Integer    | switch2 daily power consumption, measured in watt-minutes                            |
| switch1ElectricCurrent | Integer    | the switch1 electrical current measured in mA                                        |
| switch2ElectricCurrent | Integer    | the switch2 electrical current measured in mA                                        |
| calibrate              | Boolean    | determines if the open and the closed positions have been properly calibrated or not |
| position               | Integer    | the current position, 0-100                                                          |
| isStuck                | String     | determine if the roller blind is stuck                                               |
| hubDeviceId            | String     | Hub ID, equivalent to device ID                                                      |

---

## Control Commands

| deviceType       | commandType | Command     | command parameter         | Description                                                                                                                                                                                                                                                                |
| ---------------- | ----------- | ----------- | ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Relay Switch 2PM | command     | turnOn      | “1”or"2"                  | set to ON state 1 represents channel 1 2 represents channel 2                                                                                                                                                                                                              |
| Relay Switch 2PM | command     | turnOff     | “1”or"2"                  | set to OFF state 1 represents channel 1 2 represents channel 2                                                                                                                                                                                                             |
| Relay Switch 2PM | command     | toggle      | “1”or"2"                  | toggle 1 represents channel 1 2 represents channel 2state                                                                                                                                                                                                                  |
| Relay Switch 2PM | command     | setMode     | channel;mode<br>e.g `1;0` | The first item represents the switching of channel number, 1 represents channel number 1 and 2 represents channel number 2. The second item represents set the switch mode. `0`, toggle mode; `1`, edge switch mode; `2`, detached switch mode; `3`, momentary switch mode |
| Relay Switch 2PM | command     | setPosition | `0~100`                   | Set roller blind opening and closing percentage. `0`, Open All; `100`, Close All                                                                                                                                                                                           |

---

## Webhook Events

| Key Name     | Value Type | Description                                                                                             |
| ------------ | ---------- | ------------------------------------------------------------------------------------------------------- |
| eventType    | String     | the type of events                                                                                      |
| eventVersion | String     | the current event version                                                                               |
| context      | Object     | the detail info of the event                                                                            |
| deviceType   | String     | the type of the device                                                                                  |
| deviceMac    | String     | the MAC address of the device                                                                           |
| online       | Boolean    | determines if the device is connected to the internet or disconnected                                   |
| switchStatus | Integer    | the switch state of the device. `1`, on; `0`, off                                                       |
| overload     | Boolean    | determines if the device is power overloaded or not                                                     |
| calibrate    | Boolean    | determines if the open position and the close position of a device have been properly calibrated or not |
| position     | Integer    | determine the percentage of the device that is open or closed                                           |
| isStuck      | Boolean    | determine if the device is stuck                                                                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Relay Switch 2PM",
        "deviceMac": "FFFFFFFFFFF",
        "online": false,
        "overTemperature": true,
        "switch1Status": 1,
        "switch2Status": 1,
        "switch1Overload": true,
        "switch2Overload": true,
        "calibrate": true,
        "position": 0,
        "isStuck": true
    }
}
```
