# Pan/Tilt Cam Plus 3K

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Pan/Tilt Cam Plus 3K_                                                                      |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Device Status

| Key         | Value Type | Description                          |
| ----------- | ---------- | ------------------------------------ |
| deviceId    | String     | device ID                            |
| deviceType  | String     | device type. _Pan/Tilt Cam Plus 3K_  |
| hubDeviceId | String     | device's parent Hub ID               |
| latestImage | Object     | the latest snapshot image info. contains `imageUrl` and `expireAt`. an empty object when no snapshot is available |

The `latestImage` object has the following attributes.

| Key      | Value Type | Description                                                                                     |
| -------- | ---------- | ----------------------------------------------------------------------------------------------- |
| imageUrl | String     | a pre-signed URL of the latest snapshot image (taken when the latest motion event occurred)     |
| expireAt | Long       | the time stamp (in seconds) when the pre-signed URL expires. about 10 minutes after the request |

```js
{
    "deviceId": "FFFFFFFFFFFF",
    "deviceType": "Pan/Tilt Cam Plus 3K",
    "hubDeviceId": "000000000000",
    "latestImage": {
        "imageUrl": "https://...",
        "expireAt": 1789445322
    }
}
```

---

## Webhook Events

Note: the `deviceType` in webhook messages is _WoCamKvs5mp_, which is different from the one in the device list and device status.

| Key Name     | Value Type | Description                                                              |
| ------------ | ---------- | ------------------------------------------------------------------------ |
| eventType    | String     | the type of events                                                       |
| eventVersion | String     | the current event version                                                |
| context      | Object     | the detail info of the event                                             |
| deviceType   | String     | the type of the device. _WoCamKvs5mp_                                    |
| deviceMac    | String     | the MAC address of the device                                            |
| motionEvent  | Object     | sent when motion is detected. contains `detectionType`, `img`, and `startTimestamp` |
| humanEvent   | Object     | sent when a human is detected. contains `detectionType`, `img`, and `startTimestamp` |
| timeOfSample | Long       | the time stamp when the event is sent                                    |

Each event object (`motionEvent` or `humanEvent`) has the following attributes. Only one event object is included per webhook message.

| Key            | Value Type | Description                                                          |
| -------------- | ---------- | -------------------------------------------------------------------- |
| detectionType  | String     | the type of the detection, e.g. "motion" or "human"                  |
| img            | String     | a pre-signed URL of the snapshot image taken when the event occurred |
| startTimestamp | Long       | the time stamp (in seconds) when the event started                   |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoCamKvs5mp",
        "deviceMac": DEVICE_MAC_ADDR,
        "motionEvent": {
            "detectionType": "motion",
            "img": "https://...",
            "startTimestamp": 1784708706
        },
        "timeOfSample": 123456789
    }
}
```

---
