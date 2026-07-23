# Plug Mini (US)

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Plug Mini (US)_                                                                            |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key              | Value Type | Description                                                                                              |
| ---------------- | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId         | String     | device ID                                                                                                |
| deviceType       | String     | device type. _Plug Mini (US)_                                                                            |
| hubDeviceId      | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |
| voltage          | Float      | the voltage of the device, measured in Volt                                                              |
| version          | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3                                                |
| weight           | Float      | the power consumed in a day, measured in Watts                                                           |
| electricityOfDay | Integer    | the duration that the device has been used during a day, measured in minutes                             |
| electricCurrent  | Float      | the current of the device at the moment, measured in mA                                                  |

---

## Control Commands

| deviceType     | commandType | Command | command parameter | Description      |
| -------------- | ----------- | ------- | ----------------- | ---------------- |
| Plug Mini (US) | command     | turnOn  | default           | set to ON state  |
| Plug Mini (US) | command     | turnOff | default           | set to OFF state |
| Plug Mini (US) | command     | toggle  | default           | toggle state     |

---

## Webhook Events

| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | the type of the device                               |
| deviceMac    | String     | the MAC address of the device                        |
| powerState   | String     | the current power state of the device, "ON" or "OFF" |
| timeOfSample | Long       | the time stamp when the event is sent                |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoPlugUS",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "timeOfSample": 123456789
    }
}
```
