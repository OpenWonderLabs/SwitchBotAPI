# Humidifier

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Humidifier_                                                                                |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key                    | Value Type | Description                                           |
| ---------------------- | ---------- | ----------------------------------------------------- |
| deviceId               | String     | device ID                                             |
| deviceType             | String     | device type. _Humidifier_                             |
| power                  | String     | ON/OFF state                                          |
| humidity               | Integer    | humidity percentage                                   |
| temperature            | Float      | temperature in celsius                                |
| nebulizationEfficiency | Integer    | atomization efficiency percentage                     |
| auto                   | Boolean    | determines if a Humidifier is in Auto Mode or not     |
| childLock              | Boolean    | determines if a Humidifier's safety lock is on or not |
| sound                  | Boolean    | determines if a Humidifier is muted or not            |
| lackWater              | Boolean    | determines if the water tank is empty or not          |

---

## Control Commands

| deviceType | commandType | Command | command parameter                                    | Description                                                                                                                                                    |
| ---------- | ----------- | ------- | ---------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Humidifier | command     | turnOff | default                                              | set to OFF state                                                                                                                                               |
| Humidifier | command     | turnOn  | default                                              | set to ON state                                                                                                                                                |
| Humidifier | command     | setMode | `auto` or `101` or<br /> `102` or `103` or `{0~100}` | auto, set to Auto Mode,<br />101, set atomization efficiency to 34%,<br />102, set atomization efficiency to 67%,<br />103, set atomization efficiency to 100% |

---
