# Plug

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Plug_                                                                                      |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key         | Value Type | Description                                                                                              |
| ----------- | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId    | String     | device ID                                                                                                |
| deviceType  | String     | device type. _Plug_                                                                                      |
| power       | String     | ON/OFF state                                                                                             |
| version     | String     | the current Wi-Fi firmware version, e.g. V4.2                                                            |
| hubDeviceId | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Control Commands

| deviceType | commandType | Command | command parameter | Description      |
| ---------- | ----------- | ------- | ----------------- | ---------------- |
| Plug       | command     | turnOn  | default           | set to ON state  |
| Plug       | command     | turnOff | default           | set to OFF state |

---
