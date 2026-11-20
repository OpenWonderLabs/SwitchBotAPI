# AI Art Frame

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _AI Art Frame_                                          |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key         | Value Type | Description                                                 |
| ----------- | ---------- | ----------------------------------------------------------- |
| deviceId    | String     | device ID                                                   |
| deviceType  | String     | device type. _AI Art Frame_                                 |
| hubDeviceId | String     | device's parent Hub ID                                      |
| battery     | Integer    | the current battery level, 0-100                            |
| displayMode | Integer    | display mode: 0 = Static image; 1 = Slideshow               |
| imageUrl    | String     | the URL of the image currently displayed on the photo frame |
| version     | String     | the current firmware version, e.g. V0.0-0.5                 |

---

## Control Commands

| deviceType   | commandType | Command     | command parameter                                                              | Description                                            |
| ------------ | ----------- | ----------- | ------------------------------------------------------------------------------ | ------------------------------------------------------ |
| AI Art Frame | command     | next        | default                                                                        | Switch to the next image                               |
| AI Art Frame | command     | previous    | default                                                                        | Switch to the previous image                           |
| AI Art Frame | command     | deleteImage | `random`, `newest` or `oldest`                                                 | Delete one image from the photo frame. **Deleted images cannot be recovered.**<br />`random`, delete a random image.<br />`newest`, delete the most recently added image.<br />`oldest`, delete the earliest added image.<br />The image currently displayed is never deleted. Images in the cloud that have not been downloaded to the frame are included. See the response below.|
| AI Art Frame | command     | uploadImage | `{"imageUrl":"https://..."}` OR `{"imageBase64":"data:image/jpeg;base64,..."}` | Upload an image (choose one of imageUrl / imageBase64) |

#### deleteImage response

The command returns after the image is deleted in the cloud and the delete instruction is sent to the photo frame. It does not wait for the photo frame to finish.

| Key Name          | Value Type | Description                                                                                                  |
| ----------------- | ---------- | ------------------------------------------------------------------------------------------------------------ |
| deletedImageIndex | Integer    | the device index of the deleted image. `0` when no image was deleted                                         |
| remainingCount    | Integer    | the number of images remaining in the cloud, including images that have not been downloaded to the frame yet |

- When only the currently displayed image is left, nothing is deleted and the response is `deletedImageIndex: 0`, `remainingCount: 1`.
- When the album is empty, the response is `deletedImageIndex: 0`, `remainingCount: 0`.
- If the currently displayed image cannot be determined, the command fails and nothing is deleted.

```js
{
    "statusCode": 100,
    "body": {
        "deletedImageIndex": 123,
        "remainingCount": 9
    },
    "message": "success"
}
```

---

## Webhook Events

| Key Name     | Value Type | Description                                   |
| ------------ | ---------- | --------------------------------------------- |
| eventType    | String     | the type of events                            |
| eventVersion | String     | the current event version                     |
| context      | Object     | the detail info of the event                  |
| deviceType   | String     | the type of the device                        |
| deviceMac    | String     | the MAC address of the device                 |
| displayMode  | Integer    | display mode: 0 = Static image; 1 = Slideshow |
| battery      | Integer    | the current battery level, 0-100              |
| timeOfSample | Long       | the time stamp when the event is sent         |

```js
{
   "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "AI Art Frame",
        "deviceMac": "B0E9FEA5D7F0",
        "displayMode": 1, // Display mode: 0 = Static image; 1 = Slideshow
        "battery": 100,
        "timeOfSample": 123456789
    }
}

```

---

- [SwitchBot (Official website)](https://www.switch-bot.com/)
- [Facebook @SwitchBotRobot](https://www.facebook.com/SwitchBotRobot/)
- [Twitter @SwitchBot](https://twitter.com/switchbot)
