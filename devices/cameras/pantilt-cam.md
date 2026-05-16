# Pan/Tilt Cam

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Pan/Tilt Cam_                                                                              |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

---

## Webhook Events

| Key Name       | Value Type | Description                                                                 |
| -------------- | ---------- | --------------------------------------------------------------------------- |
| eventType      | String     | the type of events                                                          |
| eventVersion   | String     | the current event version                                                   |
| context        | Object     | the detail info of the event                                                |
| deviceType     | String     | the type of the device                                                      |
| deviceMac      | String     | the MAC address of the device                                               |
| detectionState | String     | the detection state of the device, "DETECTED" stands for motion is detected |
| timeOfSample   | Long       | the time stamp when the event is sent                                       |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoPanTiltCam",
        "deviceMac": DEVICE_MAC_ADDR,
        "detectionState": "DETECTED",
        "timeOfSample": 123456789
    }
}
```
