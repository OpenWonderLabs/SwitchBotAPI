# Vision Doorbell

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Vision Doorbell_                                                                           |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |
| lockDeviceId       | String     | the MAC address of the Lock bound to the doorbell. _null_ when no Lock is bound                          |

---

## Device Status

| Key         | Value Type | Description                                                           |
| ----------- | ---------- | --------------------------------------------------------------------- |
| deviceId    | String     | device ID                                                             |
| deviceType  | String     | device type. _Vision Doorbell_                                        |
| hubDeviceId | String     | device's parent Hub ID                                                |
| version     | String     | the current firmware version, e.g. V1.0                               |
| battery     | Integer    | the current battery level, 0-100                                      |
| online      | Boolean    | the connection status of the device. `true`, online; `false`, offline |

---

## Control Commands

Vision Doorbell does not support device control commands.

---

## Webhook Events

Vision Doorbell does not support webhook events.
