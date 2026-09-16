# Outdoor Pan/Tilt Cam 3K

SwitchBot Outdoor Pan/Tilt Cam 3K. Note: the `deviceType` string used by the API is the abbreviated form _Outdoor PTC 3K_.

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Outdoor PTC 3K_. Note: this key has been observed to be missing in actual device list responses. |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID                                                                                   |

---

## Device Status

| Key         | Value Type | Description                          |
| ----------- | ---------- | ------------------------------------ |
| deviceId    | String     | device ID                            |
| deviceType  | String     | device type. _Outdoor PTC 3K_        |
| hubDeviceId | String     | device's parent Hub ID               |
| latestImage | Object     | the latest snapshot image info. an empty object when no snapshot is available |

---

## Webhook Events

Note: the `deviceType` in webhook messages is _W1156000_, which is different from the one in the device status.

| Key Name     | Value Type | Description                                                              |
| ------------ | ---------- | ------------------------------------------------------------------------ |
| eventType    | String     | the type of events                                                       |
| eventVersion | String     | the current event version                                                |
| context      | Object     | the detail info of the event                                             |
| deviceType   | String     | the type of the device. _W1156000_                                       |
| deviceMac    | String     | the MAC address of the device                                            |
| humanEvent   | Object     | sent when a human is detected. contains `detectionType`, `img`, and `startTimestamp` |
| motionEvent  | Object     | sent when motion is detected. contains `detectionType`, `img`, and `startTimestamp` |
| timeOfSample | Long       | the time stamp when the event is sent                                    |

Each event object (`humanEvent` or `motionEvent`) has the following attributes. Only one event object is included per webhook message.

| Key            | Value Type | Description                                                          |
| -------------- | ---------- | -------------------------------------------------------------------- |
| detectionType  | String     | the type of the detection, e.g. "human" or "motion"                  |
| img            | String     | a pre-signed URL of the snapshot image taken when the event occurred |
| startTimestamp | Long       | the time stamp (in seconds) when the event started                   |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "W1156000",
        "deviceMac": DEVICE_MAC_ADDR,
        "humanEvent": {
            "detectionType": "human",
            "img": "https://...",
            "startTimestamp": 1784815490
        },
        "timeOfSample": 123456789
    }
}
```
