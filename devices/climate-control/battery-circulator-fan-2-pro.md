# Battery Circulator Fan 2 Pro

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Battery Circulator Fan 2 Pro_                          |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key                 | Value Type | Description                                                        |
| ------------------- | ---------- | ------------------------------------------------------------------ |
| deviceId            | String     | device ID                                                          |
| deviceType          | String     | device type. _Battery Circulator Fan 2 Pro_                        |
| hubDeviceId         | String     | device's parent Hub ID                                             |
| mode                | String     | fan mode. _direct_, _natural_, _sleep_, _hurricane_, or _custom_   |
| version             | String     | the current firmware version, e.g. V6.3                            |
| power               | String     | ON/OFF state. _on_ or _off_                                       |
| onlineStatus        | String     | the connection status. _online_ or _offline_                       |
| nightStatus         | String     | nightlight state. _on_ or _off_                                    |
| oscillation         | String     | horizontal oscillation. _on_ or _off_                              |
| verticalOscillation | String     | vertical oscillation. _on_ or _off_                                |
| chargingStatus      | String     | battery charge status. _charging_ or _uncharged_                   |
| fanSpeed            | Integer    | fan speed. 1-100                                                   |

---

## Control Commands

| deviceType                    | commandType | Command           | command parameter                            | Description                                        |
| ----------------------------- | ----------- | ----------------- | -------------------------------------------- | -------------------------------------------------- |
| Battery Circulator Fan 2 Pro  | command     | turnOff           | default                                      | set to OFF state                                   |
| Battery Circulator Fan 2 Pro  | command     | turnOn            | default                                      | set to ON state                                    |
| Battery Circulator Fan 2 Pro  | command     | setNightLightMode | `off`, `0`, or `1`                           | `off`, turn off; `0`, bright; `1`, soft            |
| Battery Circulator Fan 2 Pro  | command     | setWindMode       | `direct`, `natural`, `sleep`, or `hurricane` | set fan mode                                       |
| Battery Circulator Fan 2 Pro  | command     | setWindSpeed      | `{1-100}`, e.g. `10`                         | set fan speed                                      |

---

## Webhook Events

| Key Name            | Value Type | Description                                                        |
| ------------------- | ---------- | ------------------------------------------------------------------ |
| eventType           | String     | the type of events                                                 |
| eventVersion        | String     | the current event version                                          |
| context             | Object     | the detail info of the event                                       |
| deviceType          | String     | the type of the device                                             |
| deviceMac           | String     | the MAC address of the device                                      |
| mode                | String     | fan mode. _direct_, _natural_, _sleep_, or _hurricane_             |
| powerState          | String     | ON/OFF state                                                       |
| nightStatus         | String     | nightlight state. _on_ or _off_                                    |
| oscillation         | String     | horizontal oscillation. _on_ or _off_                              |
| verticalOscillation | String     | vertical oscillation. _on_ or _off_                                |
| fanSpeed            | Integer    | fan speed                                                          |
| timeOfSample        | Long       | the time stamp when the event is sent                              |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Battery Circulator Fan 2 Pro",
        "deviceMac": DEVICE_MAC_ADDR,
        "mode": "direct",
        "powerState": "ON",
        "nightStatus": "off",
        "oscillation": "on",
        "verticalOscillation": "on",
        "fanSpeed": 3,
        "timeOfSample": 123456789
    }
}
```
