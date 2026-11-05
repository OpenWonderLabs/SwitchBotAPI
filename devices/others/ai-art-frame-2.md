# AI Art Frame 2

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _AI Art Frame Luma_                                     |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key          | Value Type | Description                                                 |
| ------------ | ---------- | ----------------------------------------------------------- |
| deviceId     | String     | device ID                                                   |
| deviceType   | String     | device type. _AI Art Frame Luma_                            |
| hubDeviceId  | String     | device's parent Hub ID                                      |
| battery      | Integer    | the current battery level, 0-100                            |
| displayMode  | Integer    | display mode: 0 = Static image; 1 = Slideshow               |
| imageUrl     | String     | the URL of the image currently displayed on the photo frame |
| onlineStatus | String     | the connection status of the device. _online_ or _offline_  |
| version      | String     | the current firmware version, e.g. V0.7-0.7                 |

---

## Control Commands

| deviceType        | commandType | Command     | command parameter                                                              | Description                                                                                                                                                                                                                                  |
| ----------------- | ----------- | ----------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Art Frame 2    | command     | next        | default                                                                        | Switch to the next image                                                                                                                                                                                                                     |
| AI Art Frame 2    | command     | previous    | default                                                                        | Switch to the previous image                                                                                                                                                                                                                 |
| AI Art Frame 2    | command     | uploadImage | `{"imageUrl":"https://..."}` OR `{"imageBase64":"data:image/jpeg;base64,..."}` | Upload an image (choose one of imageUrl / imageBase64, do not pass both). `imageBase64` accepts a Base64 string with or without the `data:image/jpeg;base64,` prefix. Returns `statusCode` 402 when the image upload limit has been reached. |

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
        "deviceType": "AI Art Frame Luma",
        "deviceMac": "B0E9FEA5D7F0",
        "displayMode": 1, // Display mode: 0 = Static image; 1 = Slideshow
        "battery": 100,
        "timeOfSample": 123456789
    }
}
```
