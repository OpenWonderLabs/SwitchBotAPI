# Robot Vacuum Cleaner S1 Plus

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Robot Vacuum Cleaner S1 Plus_                                                              |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key           | Value Type | Description                                                                                                                                                                     |
| ------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| deviceId      | String     | device ID                                                                                                                                                                       |
| deviceName    | String     | device name                                                                                                                                                                     |
| deviceType    | String     | device type. _Robot Vacuum Cleaner S1 Plus_                                                                                                                                     |
| hubDeviceId   | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi.                                                                        |
| workingStatus | String     | the working status of the device. _StandBy_, _Clearing_, _Paused_, _GotoChargeBase_, _Charging_, _ChargeDone_, _Dormant_, _InTrouble_, _InRemoteControl_, or _InDustCollecting_ |
| onlineStatus  | String     | the connection status of the device. _online_ or _offline_                                                                                                                      |
| battery       | Integer    | the current battery level                                                                                                                                                       |

---

## Control Commands

| deviceType                   | commandType | Command  | command parameter | Description                                                           |
| ---------------------------- | ----------- | -------- | ----------------- | --------------------------------------------------------------------- |
| Robot Vacuum Cleaner S1 Plus | command     | start    | default           | start vacuuming                                                       |
| Robot Vacuum Cleaner S1 Plus | command     | stop     | default           | stop vacuuming                                                        |
| Robot Vacuum Cleaner S1 Plus | command     | dock     | default           | return to charging dock                                               |
| Robot Vacuum Cleaner S1 Plus | command     | PowLevel | `{0-3}`           | set suction power level: 0 (Quiet), 1 (Standard), 2 (Strong), 3 (MAX) |

---

## Webhook Events

| Key Name      | Value Type | Description                                                                                                                                                                                                       |
| ------------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| eventType     | String     | the type of events                                                                                                                                                                                                |
| eventVersion  | String     | the current event version                                                                                                                                                                                         |
| context       | Object     | the detail info of the event                                                                                                                                                                                      |
| deviceType    | String     | attributes of the context object. the type of the device                                                                                                                                                          |
| deviceMac     | String     | attributes of the context object. the MAC address of the device                                                                                                                                                   |
| workingStatus | String     | attributes of the context object. the working status of the device. _StandBy_, _Clearing_, _Paused_, _GotoChargeBase_, _Charging_, _ChargeDone_, _Dormant_, _InTrouble_, _InRemoteControl_, or _InDustCollecting_ |
| onlineStatus  | String     | attributes of the context object. the connection status of the device. _online_ or _offline_                                                                                                                      |
| battery       | Integer    | attributes of the context object. the battery level, range from 0 to 100                                                                                                                                          |
| timeOfSample  | Long       | attributes of the context object. the time stamp when the event is sent                                                                                                                                           |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoSweeperPlus",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus"："StandBy",
        "onlineStatus": "online",
        "battery": 100,
        "timeOfSample": 123456789
    }
}
```
