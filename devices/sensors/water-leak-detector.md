# Water Leak Detector

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Water Detector_                                                                            |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key         | Value Type | Description                                                                                              |
| ----------- | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId    | String     | device ID                                                                                                |
| deviceType  | String     | device type. _Water Detector_                                                                            |
| hubDeviceId | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |
| battery     | Integer    | the current battery level, `0-100`                                                                       |
| version     | String     | the current firmware version, e.g. V4.2                                                                  |
| status      | Integer    | `0`, dry. `1`, leak detected                                                                             |

---

## Webhook Events

| Key Name       | Value Type | Description                           |
| -------------- | ---------- | ------------------------------------- |
| eventType      | String     | the type of events                    |
| eventVersion   | String     | the current event version             |
| context        | Object     | the detail info of the event          |
| deviceType     | String     | the type of the device                |
| deviceMac      | String     | the MAC address of the device         |
| detectionState | Integer    | `0`, dry. `1`, leak detected          |
| battery        | Integer    | the current battery level, `0-100`    |
| timeOfSample   | Long       | the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Water Detector",
        "deviceMac": DEVICE_MAC_ADDR,
        "detectionState": 0,
        "battery":100,
        "timeOfSample": 123456789
    }
}
```
