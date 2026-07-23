# Bot

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Bot_                                                   |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key         | Value Type | Description                                                                                                         |
| ----------- | ---------- | ------------------------------------------------------------------------------------------------------------------- |
| deviceId    | String     | device ID                                                                                                           |
| deviceType  | String     | device type. _Bot_                                                                                                  |
| power       | String     | ON/OFF state                                                                                                        |
| battery     | Integer    | Four-segment battery level division,`<10%, shown as 9;10%~20%, shown as 19;20%~60%, shown as 59;≥60%, shown as 100` |
| version     | String     | the current firmware version, e.g. V6.3                                                                             |
| deviceMode  | String     | _pressMode_, _switchMode_, or _customizeMode_                                                                       |
| hubDeviceId | String     | device's parent Hub ID                                                                                              |

---

## Control Commands

| deviceType | commandType | Command | command parameter | Description      |
| ---------- | ----------- | ------- | ----------------- | ---------------- |
| Bot        | command     | turnOff | default           | set to OFF state |
| Bot        | command     | turnOn  | default           | set to ON state  |
| Bot        | command     | press   | default           | trigger press    |

---

## Webhook Events

| Key Name     | Value Type | Description                                                                                                                                                                                                                          |
| ------------ | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| eventType    | String     | the type of events                                                                                                                                                                                                                   |
| eventVersion | String     | the current event version                                                                                                                                                                                                            |
| context      | Object     | the detail info of the event                                                                                                                                                                                                         |
| deviceType   | String     | the type of the device                                                                                                                                                                                                               |
| deviceMac    | String     | the MAC address of the device                                                                                                                                                                                                        |
| power        | String     | the current state of the device. This state is only valid for Switch Mode, where "on" stands for on and "off" stands for off. It will return "on" or "off" in Press Mode or Customize Mode, but the returned value can be neglected. |
| timeOfSample | Long       | the time stamp when the event is sent                                                                                                                                                                                                |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoHand",
        "deviceMac": DEVICE_MAC_ADDR,
        "power": "on",//"on"or"off"
        "battery": 10,
        "deviceMode": "pressMode",//pressMode,switchMode,customizeMode
        "timeOfSample": 123456789
    }
}
```
