# Robot Vacuum K11+ Pro

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Robot Vacuum Cleaner K11 Plus Pro_                                                         |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key           | Value Type | Description                                                                                                                                                                     |
| ------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| deviceId      | String     | device ID                                                                                                                                                                       |
| deviceType    | String     | device type. _Robot Vacuum Cleaner K11 Plus Pro_                                                                                                                                |
| hubDeviceId   | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi.                                                                        |
| workingStatus | String     | the working status of the device. _StandBy_, _Clearing_, _Paused_, _GotoChargeBase_, _Charging_, _ChargeDone_, _Dormant_, _InTrouble_, _InRemoteControl_, or _InDustCollecting_ |
| onlineStatus  | String     | the connection status of the device. _online_ or _offline_                                                                                                                      |
| battery       | Integer    | the current battery level `0-100`                                                                                                                                               |
| taskType      | String     | the current task in progress. _standBy_, _explore_, _cleanAll_, _cleanArea_, _cleanRoom_, _backToCharge_, _collectDust_, _remoteControl_, _cleanWithExplorer_                   |

---

## Control Commands

| deviceType | commandType | Command     | command parameter                                                                      | Description                                                                                                                                                                                                  |
| ---------- | ----------- | ----------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| K11+ Pro   | command     | startClean  | {"action": action_str, "param": {"fanLevel": fan_level_int, "times": clean_cycle_int}} | start cleaning. <br />`action_str`, the cleaning mode, _sweep_ or _mop_.<br />`fanLevel`, the vacuum level, `1-4`.<br />`times`, the number of cycles, `1-2639999`, in theory.                               |
| K11+ Pro   | command     | pause       | default                                                                                | pause.                                                                                                                                                                                                       |
| K11+ Pro   | command     | dock        | default                                                                                | return to Auto-empty Station and charge.                                                                                                                                                                     |
| K11+ Pro   | command     | setVolume   | `0-100`                                                                                | set volume, `0-100`                                                                                                                                                                                          |
| K11+ Pro   | command     | changeParam | {"fanLevel": fan_level_int, "waterLevel": water_level_int, "times": clean_cycle_int}   | change cleaning parameters, at least one parameter is required.<br />`fanLevel`, the vacuum level, `1-4`.<br />`waterLevel`, the mop moisture level, `1-2`.<br />`times`, the number of cycles, `1-2639999`, in theory. |

---

## Webhook Events

| Key Name         | Value Type | Description                                                                                                                                                                                                       |
| ---------------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| eventType        | String     | the type of events                                                                                                                                                                                                |
| eventVersion     | String     | the current event version                                                                                                                                                                                         |
| context          | Object     | the detail info of the event                                                                                                                                                                                      |
| deviceType       | String     | attributes of the context object. the type of the device                                                                                                                                                          |
| deviceMac        | String     | attributes of the context object. the MAC address of the device                                                                                                                                                   |
| workingStatus    | String     | attributes of the context object. the working status of the device. _StandBy_, _Clearing_, _Paused_, _GotoChargeBase_, _Charging_, _ChargeDone_, _Dormant_, _InTrouble_, _InRemoteControl_, or _InDustCollecting_ |
| onlineStatus     | String     | attributes of the context object. the connection status of the device. _online_ or _offline_                                                                                                                      |
| battery          | Integer    | attributes of the context object. the battery level, range from 0 to 100                                                                                                                                          |
| waterBaseBattery | Integer    | attributes of the context object. the current battery level `0-100`                                                                                                                                               |
| taskType         | String     | attributes of the context object. the current task in progress. _standBy_, _explore_, _cleanAll_, _cleanArea_, _cleanRoom_, _deepWashing_, _backToCharge_, _drying_, _collectDust_, _remoteControl_, _cleanWithExplorer_ |
| timeOfSample     | Long       | attributes of the context object. the time stamp when the event is sent                                                                                                                                           |

Only the fields that have changed are included in the event.

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Robot Vacuum Cleaner K11 Plus Pro",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus": "StandBy",
        "onlineStatus": "online",
        "battery": 100,
        "waterBaseBattery": 100,
        "taskType": "explore",
        "timeOfSample": 123456789
    }
}
```
