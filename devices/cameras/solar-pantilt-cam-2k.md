# Solar Pan/Tilt Cam 2K

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Solar Pan/Tilt Cam 2K_                                 |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

Only the outdoor unit is returned in the device list. The paired indoor unit (W1099000) is not listed separately.

---

## Device Status

| Key                  | Value Type | Description                                                                              |
| -------------------- | ---------- | ---------------------------------------------------------------------------------------- |
| deviceId             | String     | device ID                                                                                |
| deviceType           | String     | device type. _Solar Pan/Tilt Cam 2K_                                                     |
| hubDeviceId          | String     | device's parent Hub ID                                                                   |
| version              | String     | the current firmware version, e.g. V1.0.0                                                |
| battery              | Integer    | the current battery level, 0-100                                                         |
| online               | Boolean    | the connection status of the device. _true_ or _false_                                   |
| latestImage          | Object     | the latest image captured by the camera. an empty object `{}` when no image is available |
| latestImage.imageUrl | String     | the URL of the image                                                                     |
| latestImage.expireAt | Long       | the expiration time of the image URL, Unix timestamp in seconds                          |

```js
{
    "deviceId": "AABBCCDDEEFF",
    "deviceType": "Solar Pan/Tilt Cam 2K",
    "hubDeviceId": "000000000000",
    "version": "V1.0.0",
    "battery": 100,
    "online": true,
    "latestImage": {
        "imageUrl": "https://example.com/camera.jpg",
        "expireAt": 1800000000
    }
}
```

---

## Control Commands

| deviceType            | commandType | Command                | command parameter | Description           |
| --------------------- | ----------- | ---------------------- | ----------------- | --------------------- |
| Solar Pan/Tilt Cam 2K | command     | enableMotionDetection  | default           | Set to enabled state  |
| Solar Pan/Tilt Cam 2K | command     | disableMotionDetection | default           | Set to disabled state |

---

## Webhook Events

| Key Name       | Value Type | Description                                                                                                               |
| -------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------- |
| eventType      | String     | the type of events                                                                                                        |
| eventVersion   | String     | the current event version                                                                                                 |
| context        | Object     | the detail info of the event                                                                                              |
| deviceType     | String     | the type of the device                                                                                                    |
| deviceMac      | String     | the MAC address of the device                                                                                             |
| battery        | Integer    | the battery level                                                                                                         |
| detectionState | String     | the motion state of the device. "DETECTED" stands for a person or motion is detected. not included in battery-only events |
| timeOfSample   | Long       | the time stamp when the event is sent, in milliseconds                                                                    |

An event is sent when a person or motion is detected, and when the battery level changes. "NOT_DETECTED" is not reported.

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Solar Pan/Tilt Cam 2K",
        "deviceMac": "AABBCCDDEEFF",
        "battery": 80,
        "detectionState": "DETECTED",
        "timeOfSample": 1800000000000
    }
}
```
