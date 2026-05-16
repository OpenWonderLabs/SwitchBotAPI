# Standing Circulator Fan

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Standing Circulator Fan_                               |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key                 | Value Type | Description                                                                                             |
| ------------------- | ---------- | ------------------------------------------------------------------------------------------------------- |
| deviceId            | String     | device ID                                                                                               |
| deviceType          | String     | device type. _Standing Circulator Fan_                                                                  |
| hubDeviceId         | String     | device's parent Hub ID                                                                                  |
| mode                | String     | fan mode. direct mode: _direct_; natural mode: "natural"; sleep mode: "sleep"; ultra quiet mode: "baby" |
| version             | String     | the current firmware version, e.g. V4.2                                                                 |
| power               | String     | ON/OFF state                                                                                            |
| nightStatus         | String     | set nightlight status. turn off: _off_; mode 1: _1_; mode 2: _2_                                        |
| oscillation         | String     | set horizontal oscillation. turn on: _on_; turn off: _off_                                              |
| verticalOscillation | String     | set vertical oscillation. turn on: _on_; turn off: _off_                                                |
| fanSpeed            | Integer    | fan speed. 1~100                                                                                        |
| battery             | Integer    | the current battery level                                                                               |
| chargingStatus      | String     | battery charge status. _charging_ or _uncharged_                                                        |

---

## Control Commands

| deviceType               | commandType | Command           | command parameter                       | Description                                                                                                 |
| ------------------------ | ----------- | ----------------- | --------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Standing Circulator Fan  | command     | turnOff           | default                                 | Set to OFF state                                                                                            |
| Standing Circulator Fan  | command     | turnOn            | default                                 | Set to ON state                                                                                             |
| Standing Circulator Fan  | command     | setNightLightMode | `off`, `1`, or `2`                      | `off`, turn off nightlight,<br />`1`, bright <br />`2`, dim                                                 |
| Standing Circulator Fan  | command     | setWindMode       | `direct`, `natural`, `sleep`, or `baby` | Set fan mode. `direct`: direct mode. `natural`: natural mode. `sleep`: sleep mode. `baby`: ultra quiet mode |
| Standing Circulator Fan  | command     | setWindSpeed      | `{1-100}` e.g. `10`                     | Set fan speed.1~100                                                                                         |
| Standing Circulator Fann | command     | closeDelay        | `{1-36000}` e.g. `10`                   | Set fan close time                                                                                          |

---

## Webhook Events

| Key Name            | Value Type | Description                                                                                             |
| ------------------- | ---------- | ------------------------------------------------------------------------------------------------------- |
| eventType           | String     | the type of events                                                                                      |
| eventVersion        | String     | the current event version                                                                               |
| context             | Object     | the detail info of the event                                                                            |
| deviceType          | String     | the type of the device                                                                                  |
| deviceMac           | String     | the MAC address of the device                                                                           |
| mode                | String     | fan mode. direct mode: _direct_; natural mode: "natural"; sleep mode: "sleep"; ultra quiet mode: "baby" |
| version             | String     | the current firmware version, e.g. V4.2                                                                 |
| powerState          | String     | ON/OFF state                                                                                            |
| nightStatus         | String     | set nightlight status. turn off: _off_; mode 1: _1_; mode 2: _2_                                        |
| oscillation         | String     | set horizontal oscillation. turn on: _on_; turn off: _off_                                              |
| verticalOscillation | String     | set vertical oscillation. turn on: _on_; turn off: _off_                                                |
| fanSpeed            | Integer    | fan speed. 1~100                                                                                        |
| timeOfSample        | Long       | the time stamp when the event is sent                                                                   |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Standing Fan",
        "deviceMac": DEVICE_MAC_ADDR,
        "mode":"direct" ,
        "powerState": "ON",
        "nightStatus":"off",
        "oscillation":"on",
        "verticalOscillation":"on",
        "fanSpeed":3,
        "timeOfSample": 123456789
    }
}
```
