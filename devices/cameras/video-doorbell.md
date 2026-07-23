# Video Doorbell

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Video Doorbell_                                        |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key         | Value Type | Description                                               |
| ----------- | ---------- | --------------------------------------------------------- |
| deviceId    | String     | device ID                                                 |
| deviceType  | String     | device type. _Video Doorbell_                             |
| hubDeviceId | String     | device's parent Hub ID                                    |
| version     | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| battery     | Integer    | the current battery level                                 |
| online      | Boolean    | the connection status of the device. _true_ or _false_    |

---

## Control Commands

| deviceType     | commandType | Command                | command parameter | Description           |
| -------------- | ----------- | ---------------------- | ----------------- | --------------------- |
| Video Doorbell | command     | enableMotionDetection  | default           | Set to enabled state  |
| Video Doorbell | command     | disableMotionDetection | default           | Set to disabled state |

---

## Webhook Events

| Key Name       | Value Type | Description                                                                                                                                    |
| -------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| eventType      | String     | the type of events                                                                                                                             |
| eventVersion   | String     | the current event version                                                                                                                      |
| context        | Object     | the detail info of the event                                                                                                                   |
| deviceType     | String     | the type of the device                                                                                                                         |
| deviceMac      | String     | the MAC address of the device                                                                                                                  |
| battery        | Integer    | the battery level                                                                                                                              |
| detectionState | String     | the motion state of the device, "DETECTED" stands for motion is detected; "NOT_DETECTED" stands for motion has not been detected for some time |
| timeOfSample   | Long       | the time stamp when the event is sent                                                                                                          |
| press          | Boolean    | the Doorbell button was pressed                                                                                                                |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Video Doorbell",
        "deviceMac": DEVICE_MAC_ADDR,
        "battery": 80,
        "detectionState": "DETECTED",
        "press": true,
        "timeOfSample": 123456789
    }
}
```
