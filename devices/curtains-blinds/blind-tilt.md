# Blind Tilt

---

## Device List Information

| Key                 | Value Type      | Description                                                                                                                         |
| ------------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| deviceId            | String          | device ID                                                                                                                           |
| deviceName          | String          | device name                                                                                                                         |
| deviceType          | String          | device type. _Blind Tilt_                                                                                                           |
| version             | Integer         | the version of the device                                                                                                           |
| enableCloudService  | Boolean         | determines if Cloud Service is enabled or not for the current device                                                                |
| hubDeviceId         | String          | device's parent Hub ID                                                                                                              |
| blindTiltDevicesIds | Array<deviceId> | a list of Blind Tilt device IDs such that the Blind Tilt devices are being paired or grouped                                        |
| calibrate           | Boolean         | determines if the open and the closed positions have been properly calibrated or not                                                |
| group               | Boolean         | determines if a Blind Tilt device is paired with or grouped with one or more devices of the same type or not                        |
| master              | Boolean         | determines if a Blind Tilt device is the master device or not when paired with or grouped with one or more devices of the same type |
| direction           | String          | the opening direction of a Blind Tilt device                                                                                        |
| slidePosition       | Integer         | the current position, 0-100                                                                                                         |

---

## Device Status

| Key           | Value Type | Description                                                                                                  |
| ------------- | ---------- | ------------------------------------------------------------------------------------------------------------ |
| deviceId      | String     | device ID                                                                                                    |
| deviceType    | String     | device type. _Blind Tilt_                                                                                    |
| hubDeviceId   | String     | device's parent Hub ID                                                                                       |
| version       | Integer    | the firmware version of the device                                                                           |
| calibrate     | Boolean    | determines if the open and the closed positions have been properly calibrated or not                         |
| group         | Boolean    | determines if a Blind Tilt device is paired with or grouped with one or more devices of the same type or not |
| moving        | Boolean    | determines if the device is moving or not                                                                    |
| direction     | String     | the opening direction of a Blind Tilt device                                                                 |
| slidePosition | Integer    | the current position, 0-100                                                                                  |

---

## Control Commands

| deviceType | commandType | Command     | command parameter                    | Description                                                                                                                           |
| ---------- | ----------- | ----------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- |
| Blind Tilt | command     | setPosition | direction;position<br />e.g. `up;60` | direction: up/down<br />position: 0~100 (0 means closed, 100 means open, it MUST be set to a multiple of 2. e.g. `up;48` or `up; 36`) |
| Blind Tilt | command     | fullyOpen   | default                              | Set the position of Blind Tilt to open, equivalent to setting the position to `up;100` or `down;100`                                  |
| Blind Tilt | command     | closeUp     | default                              | Set the position of Blind Tilt to closed up, equivalent to setting the position to `up;0`                                             |
| Blind Tilt | command     | closeDown   | default                              | Set the position of Blind Tilt to closed down, equivalent to setting the position to `down;0`                                         |

---
