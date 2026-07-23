# Garage Door Opener

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Garage Door Opener_                                    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key        | Value Type | Description                                               |
| ---------- | ---------- | --------------------------------------------------------- |
| deviceId   | String     | device ID                                                 |
| deviceType | String     | device type. _Garage Door Opener_                         |
| doorStatus | Integer    | the current switch state. `0`, on; `1`, off               |
| online     | Boolean    | the connection status of the device. _true_ or _false_    |
| version    | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |

---

## Control Commands

| deviceType         | commandType | Command | command parameter | Description      |
| ------------------ | ----------- | ------- | ----------------- | ---------------- |
| Garage Door Opener | command     | turnOn  | default           | set to ON state  |
| Garage Door Opener | command     | turnOff | default           | set to OFF state |

---

## Webhook Events

| Key Name     | Value Type | Description                                      |
| ------------ | ---------- | ------------------------------------------------ |
| eventType    | String     | the type of events                               |
| eventVersion | String     | the current event version                        |
| context      | Object     | the detail info of the event                     |
| deviceType   | String     | the type of the device                           |
| deviceMac    | String     | the MAC address of the device                    |
| doorStatus   | Integer    | he switch state of the device. `0`, on; `1`, off |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Garage Door Opener",
        "deviceMac": "FFFFFFFFFFF",
        "doorStatus": 1,
    }
}
```
