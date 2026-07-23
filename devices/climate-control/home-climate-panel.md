# Home Climate Panel

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Home Climate Panel_                                    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key          | Value Type | Description                                               |
| ------------ | ---------- | --------------------------------------------------------- |
| deviceId     | String     | device ID                                                 |
| deviceType   | String     | device type. _Home Climate Panel_                         |
| battery      | Integer    | the current battery level `0-100`                         |
| version      | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| temperature  | Float      | temperature in celsius                                    |
| humidity     | Integer    | humidity percentage                                       |
| moveDetected | Boolean    | determines if motion is detected                          |
| brightness   | Integer    | the brightness value, range from 1 to 100                 |

---

## Webhook Events

| Key Name       | Value Type | Description                                                                                                                                    |
| -------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| eventType      | String     | the type of events                                                                                                                             |
| eventVersion   | String     | the current event version                                                                                                                      |
| context        | Object     | the detail info of the event                                                                                                                   |
| deviceType     | String     | the type of the device                                                                                                                         |
| deviceMac      | String     | the MAC address of the device                                                                                                                  |
| temperature    | Float      | the current temperature reading                                                                                                                |
| humidity       | Integer    | the current humidity reading in percentage                                                                                                     |
| scale          | String     | the current temperature unit being used                                                                                                        |
| battery        | Integer    | the current battery level                                                                                                                      |
| detectionState | String     | the motion state of the device, "DETECTED" stands for motion is detected; "NOT_DETECTED" stands for motion has not been detected for some time |
| brightness     | String     | the brightness level. "bright" or "dim"                                                                                                        |
| timeOfSample   | Long       | the time stamp when the event is sent                                                                                                          |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "climate Panel",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature":13,
        "humidity":18,
        "scale": "CELSIUS",
        "battery":100,
        "detectionState": "DETECTED",
        "brightness":"bright" // bright,dim
        "timeOfSample": 123456789
    }
}

```
