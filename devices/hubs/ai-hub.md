# AI Hub

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _AI Hub_                                                                                    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key          | Value Type | Description                                                                                  |
| ------------ | ---------- | -------------------------------------------------------------------------------------------- |
| deviceId     | String     | device ID                                                                                    |
| deviceType   | String     | device type. _AI Hub_                                                                        |
| hubDeviceId  | String     | device's parent Hub ID                                                                       |
| version      | String     | the current firmware version, e.g. V4.2                                                      |
| onlineStatus | String     | attributes of the context object. the connection status of the device. _online_ or _offline_ |

---
