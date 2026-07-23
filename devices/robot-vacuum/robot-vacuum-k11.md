# Robot Vacuum K11+

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Robot Vacuum Cleaner K11+_                                                                 |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key                | Value Type | Description                                                                                                                                                                                                                                                |
| ------------------ | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                                                                                                                                                                  |
| deviceName         | String     | device name                                                                                                                                                                                                                                                |
| deviceType         | String     | device type. _Robot Vacuum Cleaner K11+_                                                                                                                                                                                                                   |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                                                                                                                                                                       |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi.                                                                                                                                                   |
| workingStatus      | String     | the working status of the device. _StandBy_, _Clearing_, _Paused_, _GotoChargeBase_, _Charging_, _ChargeDone_, _Dormant_, _InTrouble_, _InRemoteControl_, or _InDustCollecting_                                                                            |
| onlineStatus       | String     | the connection status of the device. _online_ or _offline_                                                                                                                                                                                                 |
| battery            | Integer    | the current battery level `0-100`                                                                                                                                                                                                                          |
| taskType           | String     | the current task in progress. _standBy_, _explore_, _cleanAll_, _cleanArea_, _cleanRoom_, _fillWater_, _deepWashing_, _backToCharge_, _markingWaterBase_, _drying_, _collectDust_, _remoteControl_, _cleanWithExplorer_, _fillWaterForHumi_, _markingHumi_ |

---

## Control Commands

| deviceType | commandType | Command     | command parameter                                                                      | Description                                                                                                                                                                    |
| ---------- | ----------- | ----------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| K11+       | command     | startClean  | {"action": action_str, "param": {"fanLevel": fan_level_int, "times": clean_cycle_int}} | start cleaning. <br />`action_str`, the cleaning mode, _sweep_ or _mop_.<br />`fanLevel`, the vacuum level, `1-4`.<br />`times`, the number of cycles, `1-2639999`, in theory. |
| K11+       | command     | pause       | default                                                                                | pause.                                                                                                                                                                         |
| K11+       | command     | dock        | default                                                                                | return to Auto-empty Station and charge.                                                                                                                                       |
| K11+       | command     | setVolume   | `0-100`                                                                                | set volume, `1-100`                                                                                                                                                            |
| K11+       | command     | changeParam | {"fanLevel": fan_level_int, "waterLevel": water_level_int, "times": clean_cycle_int}   | `fanLevel`, the vacuum level, `1-4`.<br />`waterLevel`, the mop moisture level, `1-2`.<br />`times`, the number of cycles, `1-2639999`, in theory.                             |

---

## Webhook Events

| Key Name      | Value Type | Description                                                                                                                                                                                                                                                |
| ------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| eventType     | String     | the type of events                                                                                                                                                                                                                                         |
| eventVersion  | String     | the current event version                                                                                                                                                                                                                                  |
| context       | Object     | the detail info of the event                                                                                                                                                                                                                               |
| deviceType    | String     | attributes of the context object. the type of the device                                                                                                                                                                                                   |
| deviceMac     | String     | attributes of the context object. the MAC address of the device                                                                                                                                                                                            |
| workingStatus | String     | attributes of the context object. the working status of the device. _StandBy_, _Clearing_, _Paused_, _GotoChargeBase_, _Charging_, _ChargeDone_, _Dormant_, _InTrouble_, _InRemoteControl_, or _InDustCollecting_                                          |
| onlineStatus  | String     | attributes of the context object. the connection status of the device. _online_ or _offline_                                                                                                                                                               |
| battery       | Integer    | attributes of the context object. the battery level, range from 0 to 100                                                                                                                                                                                   |
| taskType      | String     | the current task in progress. _standBy_, _explore_, _cleanAll_, _cleanArea_, _cleanRoom_, _fillWater_, _deepWashing_, _backToCharge_, _markingWaterBase_, _drying_, _collectDust_, _remoteControl_, _cleanWithExplorer_, _fillWaterForHumi_, _markingHumi_ |
| timeOfSample  | Long       | attributes of the context object. the time stamp when the event is sent                                                                                                                                                                                    |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Robot Vacuum Cleaner K11 Plus",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus"："StandBy",
        //StandBy,Clearing,Paused,GotoChargeBase,Charging,ChargeDone,Dormant,InTrouble,InRemoteControl,InDustCollecting
        "onlineStatus": "online",//online,offline
        "battery": 100,// 0-100
        "taskType": "explore", // standBy,explore,cleanAll,cleanArea,cleanRoom,deepWashing,backToCharge,drying,collectDust,remoteControl,cleanWithExplorer
        "timeOfSample": 123456789
    }
}
```
