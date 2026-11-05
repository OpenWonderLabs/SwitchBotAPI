# RGBICWW Ceiling Light

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _RGBICWW Ceiling Light_                                 |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

---

## Device Status

| Key                  | Value Type | Description                                                |
| -------------------- | ---------- | ---------------------------------------------------------- |
| deviceId             | String     | device ID                                                  |
| deviceType           | String     | device type. _RGBICWW Ceiling Light_                       |
| hubDeviceId          | String     | device's parent Hub ID                                     |
| version              | String     | the current firmware version, e.g. V6.3                    |
| power                | String     | total power state. _on_, _off_, or _partial_               |
| onlineStatus         | String     | the connection status. _online_ or _offline_               |
| mainLightPower       | String     | main light power state. _on_ or _off_                      |
| mainLightBrightness  | Integer    | main light brightness                                      |
| mainLightColorTemp   | Integer    | main light color temperature                               |
| colorLightPower      | String     | color light power state. _on_ or _off_                     |
| colorLightBrightness | Integer    | color light brightness                                     |
| colorLightRGB        | String     | color light RGB value                                      |

---

## Control Commands

| deviceType            | commandType | Command                 | command parameter           | Description                |
| --------------------- | ----------- | ----------------------- | --------------------------- | -------------------------- |
| RGBICWW Ceiling Light | command     | turnOn                  | default                     | turn on all lights         |
| RGBICWW Ceiling Light | command     | turnOff                 | default                     | turn off all lights        |
| RGBICWW Ceiling Light | command     | toggle                  | default                     | toggle all lights          |
| RGBICWW Ceiling Light | command     | turnOnMainLight         | default                     | turn on main light         |
| RGBICWW Ceiling Light | command     | turnOffMainLight        | default                     | turn off main light        |
| RGBICWW Ceiling Light | command     | turnOnColorLight        | default                     | turn on color light        |
| RGBICWW Ceiling Light | command     | turnOffColorLight       | default                     | turn off color light       |
| RGBICWW Ceiling Light | command     | setMainLightBrightness  | `{1-100}`                   | set main light brightness  |
| RGBICWW Ceiling Light | command     | setMainLightColorTemp   | `{2700-6500}`               | set main light color temp  |
| RGBICWW Ceiling Light | command     | setColorLightBrightness | `{1-100}`                   | set color light brightness |
| RGBICWW Ceiling Light | command     | setColorLightRGB        | `"{0-255}:{0-255}:{0-255}"` | set color light RGB value  |
| RGBICWW Ceiling Light | command | setLightEffect | `{"effectId": effect_id_int}`<br>`effect_id_int`: Integer, required, `0–25`<br>`0`: Romance<br>`1`: Vitality<br>`2`: Heartthrob<br>`3`: Party<br>`4`: Dynamic<br>`5`: Mystery<br>`6`: Lightning<br>`7`: Rock<br>`8`: Starlight<br>`9`: Valentine's Day<br>`10`: Dream<br>`11`: Alarm<br>`12`: Fireworks<br>`13`: Waves<br>`14`: Christmas<br>`15`: Rainbow<br>`16`: Game<br>`17`: Halloween<br>`18`: Meditation<br>`19`: Starlit Sky<br>`20`: Sleep<br>`21`: Film<br>`22`: Sunrise<br>`23`: Sunset<br>`24`: New Year<br>`25`: Cherry Blossom | set a preset light effect for the color light. Example: `{"effectId": 1}` selects Vitality. |

---

## Webhook Events

| Key Name             | Value Type | Description                           |
| -------------------- | ---------- | ------------------------------------- |
| eventType            | String     | the type of events                    |
| eventVersion         | String     | the current event version             |
| context              | Object     | the detail info of the event          |
| deviceType           | String     | the type of the device                |
| deviceMac            | String     | the MAC address of the device         |
| powerState           | String     | main light state. _ON_ or _OFF_       |
| brightness           | Integer    | main light brightness                 |
| colorTemperature     | Integer    | main light color temperature          |
| colorLightPowerState | String     | color light state. _ON_ or _OFF_      |
| colorLightBrightness | Integer    | color light brightness                |
| colorLightColor      | String     | color light RGB value                 |
| timeOfSample         | Long       | the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "RGBICWW Ceiling Light",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "brightness": 10,
        "colorTemperature": 3000,
        "colorLightPowerState": "ON",
        "colorLightBrightness": 30,
        "colorLightColor": "255:134:3",
        "timeOfSample": 123456789
    }
}
```
