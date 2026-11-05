# Universal Remote

SwitchBot Universal Remote (screen-equipped learning remote). Note: the `deviceType` string is all lowercase, _remote with screen_.

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _remote with screen_                                                                        |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key            | Value Type | Description                                       |
| -------------- | ---------- | ------------------------------------------------- |
| deviceId       | String     | device ID                                         |
| deviceType     | String     | device type. _remote with screen_                 |
| hubDeviceId    | String     | device's parent Hub ID                            |
| version        | String     | the current firmware version, e.g. V4.8           |
| battery        | Integer    | the current battery level, `0-100`                |
| chargingStatus | String     | battery charge status. _charging_ or _uncharged_  |
