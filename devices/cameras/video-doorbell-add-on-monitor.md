# Video Doorbell Add-on Monitor

[SwitchBot Video Doorbell Add-on Monitor](https://www.switch-bot.com/products/switchbot-smart-video-doorbell-add-on-monitor). Appears in the device list as a separate entry from the [Video Doorbell](video-doorbell.md) it is paired with.

---

## Device List Information

Note: no `deviceType` key has been observed in the device list entry for this device.

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

```js
{
    "deviceId": "FFFFFFFFFFFF",
    "deviceName": "Add-on Monitor 40",
    "enableCloudService": false,
    "hubDeviceId": "000000000000"
}
```

---

## Device Status

The get device status endpoint responds with `statusCode` 100 and an empty `body` object for this device.

```js
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```
