# Air Purifier Table VOC

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Air Purifier Table VOC_                                |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | returns `null` if not a bluetooth device                             |

---

## Device Status

| Key         | Value Type | Description                                                                               |
| ----------- | ---------- | ----------------------------------------------------------------------------------------- |
| deviceId    | String     | device ID                                                                                 |
| deviceType  | String     | device type. _Air Purifier Table VOC_                                                     |
| power       | String     | current state; `ON`, on; `OFF`, off                                                       |
| version     | String     | the current firmware version, e.g. V4.2                                                   |
| hubDeviceId | String     | returns `null` if not a bluetooth device                                                  |
| mode        | Integter   | the current mode. `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode |
| childLock   | Integter   | child lock. `0`, disabled; `1`, enabled                                                   |

---

## Control Commands

| deviceType             | commandType | Command      | command parameter                            | Description                                                                                                                                                                          |
| ---------------------- | ----------- | ------------ | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Air Purifier Table VOC | command     | turnOff      | default                                      | set to OFF state                                                                                                                                                                     |
| Air Purifier Table VOC | command     | turnOn       | default                                      | set to ON state                                                                                                                                                                      |
| Air Purifier Table VOC | command     | setMode      | {"mode": mode_int, "fanGear": fan_level_int} | set the mode. `mode_int`, `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode; `fan_level_int`, the fan level can only be set if `mode_int` is set to `1`, `1~3` |
| Air Purifier Table VOC | command     | setChildLock | `0` or `1`                                   | enable or disable child lock. `1`, enable; `0`, disable                                                                                                                              |

---

## Webhook Events

| Key Name     | Value Type | Description                                                                               |
| ------------ | ---------- | ----------------------------------------------------------------------------------------- |
| eventType    | String     | the type of events                                                                        |
| eventVersion | String     | the current event version                                                                 |
| context      | Object     | the detail info of the event                                                              |
| deviceType   | String     | the type of the device                                                                    |
| deviceMac    | String     | the MAC address of the device                                                             |
| power        | String     | the power state of the device                                                             |
| mode         | Integer    | the current mode. `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode |
| childLock    | Integer    | child lock. `0`, disabled; `1`, enabled                                                   |
| timeOfSample | Long       | the time stamp when the event is sent                                                     |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Air Purifier Table VOC",
        "deviceMac": DEVICE_MAC_ADDR,
        "power": "ON",
        "mode": 4,
        "childLock": 0,
        "timeOfSample": 123456789
    }
}
```
