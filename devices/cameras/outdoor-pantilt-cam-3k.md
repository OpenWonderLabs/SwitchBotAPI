# Outdoor Pan/Tilt Cam 3K

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Outdoor Pan/Tilt Cam 3K_                               |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key                  | Value Type | Description                                                                              |
| -------------------- | ---------- | ---------------------------------------------------------------------------------------- |
| deviceId             | String     | device ID                                                                                |
| deviceType           | String     | device type. _Outdoor Pan/Tilt Cam 3K_                                                   |
| hubDeviceId          | String     | device's parent Hub ID                                                                   |
| latestImage          | Object     | the latest image captured by the camera. an empty object `{}` when no image is available |
| latestImage.imageUrl | String     | the URL of the image                                                                     |
| latestImage.expireAt | Long       | the expiration time of the image URL, Unix timestamp in seconds                          |

```js
{
    "deviceId": "112233445566",
    "deviceType": "Outdoor Pan/Tilt Cam 3K",
    "hubDeviceId": "000000000000",
    "latestImage": {
        "imageUrl": "https://example.com/camera.jpg",
        "expireAt": 1800000000
    }
}
```
