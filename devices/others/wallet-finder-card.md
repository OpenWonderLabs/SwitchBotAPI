# Wallet Finder Card

---

## Device List Information

| Key                | Value Type | Description                                                                                              |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                                                                |
| deviceName         | String     | device name                                                                                              |
| deviceType         | String     | device type. _Wallet Finder Card_                                                                        |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device                                     |
| hubDeviceId        | String     | device's parent Hub ID. _000000000000_ when the device itself is a Hub or it is connected through Wi-Fi. |

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
