# Evaporative Humidifier

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Humidifier2_                                           |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | returns `null` if not a bluetooth device                             |

---

## Device Status

| Key           | Value Type | Description                                                                                                                                                                                                              |
| ------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| deviceId      | String     | device ID                                                                                                                                                                                                                |
| deviceType    | String     | device type. _Humidifier2_                                                                                                                                                                                               |
| power         | String     | ON/OFF state                                                                                                                                                                                                             |
| humidity      | Integer    | humidity percentage                                                                                                                                                                                                      |
| mode          | Integer    | the current mode. `1`, level 4; `2`, level 3; `3`, level 2; `4`, level 1; `5`, humidity mode; `6`, sleep mode; `7`, auto mode; `8`, drying mode                                                                          |
| drying        | Boolean    | determines if the device is drying its filter or not                                                                                                                                                                     |
| childLock     | Boolean    | determines if the safety lock is on or not                                                                                                                                                                               |
| filterElement | Object     | contains status info of the filter. e.g. {"effectiveUsageHours": 240, "usedHours": 20}. `effectiveUsageHours`, the effective duration of the filter in hours; `usedHours`, the number of hours the filter has been used. |
| version       | Integer    | firmware version                                                                                                                                                                                                         |

---

## Control Commands

| deviceType  | commandType | Command      | command parameter                                  | Description                                                                                                                                                                                                                  |
| ----------- | ----------- | ------------ | -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Humidifier2 | command     | turnOff      | default                                            | set to OFF state                                                                                                                                                                                                             |
| Humidifier2 | command     | turnOn       | default                                            | set to ON state                                                                                                                                                                                                              |
| Humidifier2 | command     | setMode      | {"mode": mode_int, "targetHumidify": humidity_int} | set the mode. `mode_int`, `1`, level 4; `2`, level 3; `3`, level 2; `4`, level 1; `5`, humidity mode; `6`, sleep mode; `7`, auto mode; `8`, drying mode; `targetHumidify`, the target humidity level in percentage, `0~100`. |
| Humidifier2 | command     | setChildLock | `true` or `false`                                  | enable or disable child lock. `true`, enable; `false`, disable                                                                                                                                                               |

---

## Webhook Events

| Key Name     | Value Type | Description                                                                                                                                     |
| ------------ | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| eventType    | String     | the type of events                                                                                                                              |
| eventVersion | String     | the current event version                                                                                                                       |
| context      | Object     | the detail info of the event                                                                                                                    |
| deviceType   | String     | the type of the device                                                                                                                          |
| deviceMac    | String     | the MAC address of the device                                                                                                                   |
| power        | String     | the power state of the device                                                                                                                   |
| mode         | Integer    | the current mode. `1`, level 4; `2`, level 3; `3`, level 2; `4`, level 1; `5`, humidity mode; `6`, sleep mode; `7`, auto mode; `8`, drying mode |
| drying       | Boolean    | determines if the device is drying its filter or not                                                                                            |
| timeOfSample | Long       | the time stamp when the event is sent                                                                                                           |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Humidifier2",
        "deviceMac": DEVICE_MAC_ADDR,
        "power": "on",
        "mode": 1,
        "drying": false,
        "timeOfSample": 123456789
    }
}
```
