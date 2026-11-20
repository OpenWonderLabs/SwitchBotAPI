# Floor Cleaning Robot S30

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Robot Vacuum Cleaner S30_                                                                  |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key              | Value Type | Description                                                                                                                                                                                                                                                |
| ---------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| deviceId         | String     | device ID                                                                                                                                                                                                                                                  |
| deviceType       | String     | device type. _Robot Vacuum Cleaner S30_                                                                                                                                                                                                                    |
| hubDeviceId      | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi.                                                                                                                                                   |
| workingStatus    | String     | the working status of the device. _StandBy_, _Clearing_, _Paused_, _GotoChargeBase_, _Charging_, _ChargeDone_, _InTrouble_, _InRemoteControl_, or _InDustCollecting_                                                                                       |
| onlineStatus     | String     | the connection status of the device. _online_ or _offline_                                                                                                                                                                                                 |
| battery          | Integer    | the current battery level `0-100`                                                                                                                                                                                                                          |
| waterBaseBattery | Integer    | the current battery level of the water base `0-100`                                                                                                                                                                                                        |
| taskType         | String     | the current task in progress. _standBy_, _explore_, _cleanAll_, _cleanArea_, _cleanRoom_, _fillWater_, _deepWashing_, _backToCharge_, _markingWaterBase_, _drying_, _collectDust_, _remoteControl_, _cleanWithExplorer_, _fillWaterForHumi_, _markingHumi_ |

---

## Control Commands

| deviceType | commandType | Command     | command parameter                                                                                                         | Description                                                                                                                                                                                               |
| ---------- | ----------- | ----------- | ------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| S30        | command     | startClean  | {"action": clean_mode_str, "param": {"fanLevel": fan_level_int, "waterLevel": water_level_int, "times": clean_cycle_int}} | start cleaning.<br />`action`, the cleaning mode, _sweep_ or _sweep_mop_.<br />`fanLevel`, the vacuum level, `1-4`.<br />`waterLevel`, the mop moisture level, `1-2`.<br />`times`, the number of cycles. |
| S30        | command     | pause       | default                                                                                                                   | pause.                                                                                                                                                                                                    |
| S30        | command     | dock        | default                                                                                                                   | return to the base station and charge.                                                                                                                                                                    |
| S30        | command     | setVolume   | `0-100`                                                                                                                   | set volume, `0-100`                                                                                                                                                                                       |
| S30        | command     | selfClean   | `1`, `2`, `3` or `4`                                                                                                      | must be a number.<br />mode `1`, wash the mop.<br />mode `2`, start drying.<br />mode `3`, stop drying.<br />mode `4`, empty the dustbin.                                                                 |
| S30        | command     | changeParam | {"fanLevel": fan_level_int, "waterLevel": water_level_int, "times": clean_cycle_int}                                      | `fanLevel`, the vacuum level, `1-4`.<br />`waterLevel`, the mop moisture level, `1-2`.<br />`times`, the number of cycles.                                                                                |

---

## Webhook Events

| Key Name         | Value Type | Description                                                                                                                                                                                                                                                |
| ---------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| eventType        | String     | the type of events                                                                                                                                                                                                                                         |
| eventVersion     | String     | the current event version                                                                                                                                                                                                                                  |
| context          | Object     | the detail info of the event                                                                                                                                                                                                                               |
| deviceType       | String     | the type of the device                                                                                                                                                                                                                                     |
| deviceMac        | String     | the MAC address of the device                                                                                                                                                                                                                              |
| workingStatus    | String     | the working status of the device. _StandBy_, _Clearing_, _Paused_, _GotoChargeBase_, _Charging_, _ChargeDone_, _InTrouble_, _InRemoteControl_, or _InDustCollecting_                                                                                       |
| onlineStatus     | String     | the connection status of the device. _online_ or _offline_                                                                                                                                                                                                 |
| battery          | Integer    | the current battery level `0-100`                                                                                                                                                                                                                          |
| waterBaseBattery | Integer    | the current battery level of the water base `0-100`                                                                                                                                                                                                        |
| taskType         | String     | the current task in progress. _standBy_, _explore_, _cleanAll_, _cleanArea_, _cleanRoom_, _fillWater_, _deepWashing_, _backToCharge_, _markingWaterBase_, _drying_, _collectDust_, _remoteControl_, _cleanWithExplorer_, _fillWaterForHumi_, _markingHumi_ |
| timeOfSample     | Long       | the time stamp in Unix milliseconds when the event is sent                                                                                                                                                                                                 |

Only the properties that have changed are included in each event, together with `deviceType`, `deviceMac` and `timeOfSample`.

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Robot Vacuum Cleaner S30",
        "deviceMac": "AABBCCDDEEFF",
        "workingStatus": "Clearing",
        "onlineStatus": "online",
        "battery": 83,
        "waterBaseBattery": 100,
        "taskType": "cleanAll",
        "timeOfSample": 1794441600000
    }
}
```
