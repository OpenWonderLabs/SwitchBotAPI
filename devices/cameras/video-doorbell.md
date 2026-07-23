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
| version     | String     | the current firmware version, e.g. V2.02.033              |
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

| Key Name     | Value Type | Description                                                                                              |
| ------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| eventType    | String     | the type of events                                                                                       |
| eventVersion | String     | the current event version                                                                                |
| context      | Object     | the detail info of the event                                                                             |
| deviceType   | String     | the type of the device                                                                                   |
| deviceMac    | String     | the MAC address of the device                                                                            |
| battery      | Integer    | the battery level                                                                                        |
| humanEvent   | Object     | sent when a human is detected. contains `detectionType`, `eventTime`, `id`, and `img`                    |
| ringEvent    | Object     | sent when the doorbell button is pressed. contains `detectionType`, `eventTime`, `id`, and `img`         |
| motionEvent  | Object     | sent when motion is detected. contains `detectionType`, `eventTime`, `id`, and `img`                     |
| timeOfSample | Long       | the time stamp when the event is sent                                                                    |

Each event object (`humanEvent`, `ringEvent`, or `motionEvent`) has the following attributes. Only one event object is included per webhook message.

| Key           | Value Type | Description                                                          |
| ------------- | ---------- | -------------------------------------------------------------------- |
| detectionType | String     | the type of the detection, e.g. "human" or "motion"                  |
| eventTime     | Long       | the time stamp (in seconds) when the event occurred                  |
| id            | String     | the unique ID of the event                                           |
| img           | String     | a pre-signed URL of the snapshot image taken when the event occurred |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Video Doorbell",
        "deviceMac": DEVICE_MAC_ADDR,
        "battery": 100,
        "ringEvent": {
            "detectionType": "human",
            "eventTime": 1784716196,
            "id": "a1fbf2a3-f6ca-4b81-9c1a-021a1f17c041",
            "img": "https://..."
        },
        "timeOfSample": 123456789
    }
}
```
