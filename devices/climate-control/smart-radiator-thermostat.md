# Smart Radiator Thermostat

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Smart Radiator Thermostat_                                                                 |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key         | Value Type | Description                                                                                                                                    |
| ----------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| battery     | Integer    | the current battery level                                                                                                                      |
| deviceId    | String     | device ID                                                                                                                                      |
| deviceType  | String     | device type. _Smart Radiator Thermostat_                                                                                                       |
| hubDeviceId | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi.                                       |
| mode        | Integter   | the current mode. `0`, schedule mode; `1`,manual mode; `2`, power off mode; `3`, energy saving mode; `4`, comfort mode;`5`, quick heating mode |
| temperature | Float      | temperature in celsius                                                                                                                         |
| version     | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3                                                                                      |

---

## Control Commands

| deviceType                | commandType | Command                  | command parameter | Description                                                                                                                                           |
| ------------------------- | ----------- | ------------------------ | ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Smart Radiator Thermostat | command     | turnOn                   | default           | set to ON state                                                                                                                                       |
| Smart Radiator Thermostat | command     | turnOff                  | default           | set to OFF state                                                                                                                                      |
| Smart Radiator Thermostat | command     | setMode                  | `0~5`             | set the switch mode. `0`,`0`, schedule mode; `1`,manual mode; `2`, power off mode; `3`, energy saving mode; `4`, comfort mode;`5`, quick heating mode |
| Smart Radiator Thermostat | command     | setManualModeTemperature | `4~35`            | set the radiator thermostat temperature. Temperature range: 4–35 °C (inclusive)                                                                       |

---

## Webhook Events

| Key Name     | Value Type | Description                                                             |
| ------------ | ---------- | ----------------------------------------------------------------------- |
| eventType    | String     | the type of events                                                      |
| eventVersion | String     | the current event version                                               |
| context      | Object     | the detail info of the event                                            |
| deviceType   | String     | attributes of the context object. the type of the device                |
| deviceMac    | String     | attributes of the context object. the MAC address of the device         |
| mode         | String     | set the current device mode                                             |
| battery      | Integer    | the battery level                                                       |
| timeOfSample | Long       | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Smart Radiator Thermostat",
        "deviceMac": "94A990502B72",
        "mode": 1,
        "battery": 100,
        "timeOfSample": 123456789
    }
}
```
