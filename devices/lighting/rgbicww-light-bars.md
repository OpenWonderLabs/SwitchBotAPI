# RGBICWW Light Bars

---

## Device List Information

| Key | Value Type | Description |
| --- | --- | --- |
| deviceId | String | device ID |
| deviceName | String | device name |
| deviceType | String | device type. _RGBICWW Light Bars_ |
| enableCloudService | Boolean | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId | String | device's parent Hub ID |

---

## Device Status

| Key | Value Type | Description |
| --- | --- | --- |
| deviceId | String | device ID |
| deviceType | String | device type. _RGBICWW Light Bars_ |
| hubDeviceId | String | device's parent Hub ID |
| version | String | the current Wi-Fi firmware version, e.g. V3.1 |
| power | String | ON/OFF state |
| onlineStatus | String | the connection status. _online_ or _offline_ |
| brightness | Integer | the brightness value, range from 0 to 100 |
| color | String | the color value, RGB `"255:255:255"` |
| colorTemperature | Integer | the color temperature value, range from 2700 to 6500 |

---

## Control Commands

| deviceType | commandType | Command | command parameter | Description |
| --- | --- | --- | --- | --- |
| RGBICWW Light Bars | command | turnOff | default | set to OFF state |
| RGBICWW Light Bars | command | turnOn | default | set to ON state |
| RGBICWW Light Bars | command | toggle | default | toggle state |
| RGBICWW Light Bars | command | setBrightness | `{0-100}` | set brightness |
| RGBICWW Light Bars | command | setColorTemperature | `{2700-6500}` | set color temperature |
| RGBICWW Light Bars | command | setColor | `"{0-255}:{0-255}:{0-255}"` | set RGB color value |
| RGBICWW Light Bars | command | setBrightnessAndTemperature | `{"brightness": {1-100}, "temperature": {2700-6500}}` | set brightness and color temperature; the source example uses `brightness: 0`, which conflicts with the inline `1-100` range |
| RGBICWW Light Bars | command | setMusicColorMode | `{"colorList": ["{0-255}:{0-255}:{0-255}"]}` | set music-mode colors |
| RGBICWW Light Bars | command | setMusicParamMode | `{"musicMode": {0-5}, "musicLevel": {1-100}, "sensitivity": {1-100}, "controllerMode": 0, 1, or 2}` | set music-mode parameters |
| RGBICWW Light Bars | command | setEffectColorMode | `{"style": Integer, "colorList": ["{0-255}:{0-255}:{0-255}"]}` | set effect colors; the `style` enumeration is referenced by the source but not present in the command table |
| RGBICWW Light Bars | command | setEffectSpeedMode | `{"speed": {1-255}}` | set effect speed |
| RGBICWW Light Bars | command | setSegmentColorMode | `{"color": "{0-255}:{0-255}:{0-255}", "lightIndex": {0-11}}` | set a Light Bars segment color |
| RGBICWW Light Bars | command | setLightEffect | `{"effectId": Integer}`<br>`effectId`: required, `0–25`<br>`0`: Romance<br>`1`: Vitality<br>`2`: Heartthrob<br>`3`: Party<br>`4`: Dynamic<br>`5`: Mystery<br>`6`: Lightning<br>`7`: Rock<br>`8`: Starlight<br>`9`: Valentine's Day<br>`10`: Dream<br>`11`: Alarm<br>`12`: Fireworks<br>`13`: Waves<br>`14`: Christmas<br>`15`: Rainbow<br>`16`: Game<br>`17`: Halloween<br>`18`: Meditation<br>`19`: Starlit Sky<br>`20`: Sleep<br>`21`: Film<br>`22`: Sunrise<br>`23`: Sunset<br>`24`: New Year<br>`25`: Cherry Blossom | set a preset light effect |

---

## Webhook Events

| Key Name | Value Type | Description |
| --- | --- | --- |
| eventType | String | the type of events |
| eventVersion | String | the current event version |
| context | Object | the detail info of the event |
| deviceType | String | the type of the device |
| deviceMac | String | the MAC address of the device |
| powerState | String | ON/OFF state |
| brightness | Integer | the brightness value |
| color | String | the color value, RGB `"255:255:255"` |
| colorTemperature | Integer | the color temperature value |
| timeOfSample | Long | the time stamp when the event is sent |
