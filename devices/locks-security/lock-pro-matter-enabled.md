# Lock Pro Matter Enabled

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Smart Lock Pro Wifi_                                   |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |

Device status example (GET `/v1.1/devices/{deviceId}/status`),

```json
{
  "deviceId": "FFFFFFFFFFF",
  "deviceType": "Smart Lock Pro Wifi",
  "hubDeviceId": "FFFFFFFFFFF",
  "battery": 100,
  "version": "V6.3",
  "lockState": "unlock",
  "doorState": "open",
  "calibrate": true
}
```

`lockState` can be `jammed`, `unlock`, `lock`, `latchBoltLocked`.
`doorState` can be `open` or `close`.

---

## Device Status

| Key          | Value Type | Description                                                |
| ------------ | ---------- | ---------------------------------------------------------- |
| deviceId     | String     | device ID                                                  |
| deviceType   | String     | device type. _Smart Lock Pro Wifi_                         |
| hubDeviceId  | String     | device's parent Hub ID                                     |
| battery      | Integer    | the current battery level, 0-100                           |
| version      | String     | the current firmware version, e.g. V6.3                    |
| lockState    | String     | jammed, unlock, lock, latchBoltLocked                      |
| doorState    | String     | open, close                                                |
| calibrate    | Boolean    | determines if Lock has been calibrated or not              |
| onlineStatus | String     | the connection status of the device. _online_ or _offline_ |

---

## Control Commands

| deviceType          | commandType | Command          | command parameter | Description                 |
| ------------------- | ----------- | ---------------- | ----------------- | --------------------------- |
| Smart Lock Pro Wifi | command     | lock             | default           | rotate to locked position   |
| Smart Lock Pro Wifi | command     | unlock           | default           | rotate to unlocked position |
| Smart Lock Pro Wifi | command     | nightLatchUnlock | default           | unlock night latch (EU)     |
| Smart Lock Pro Wifi | command     | deadbolt         | default           | disengage deadbolt or latch |

---

## Webhook Events

| Key Name     | Value Type | Description                                                                                                                                                                                                     |
| ------------ | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| eventType    | String     | the type of events                                                                                                                                                                                              |
| eventVersion | String     | the current event version                                                                                                                                                                                       |
| context      | Object     | the detail info of the event                                                                                                                                                                                    |
| deviceType   | String     | the type of the device                                                                                                                                                                                          |
| deviceMac    | String     | the MAC address of the device                                                                                                                                                                                   |
| lockState    | String     | the state of the device, "LOCKED" stands for the motor is rotated to locking position; "UNLOCKED" stands for the motor is rotated to unlocking position; "JAMMED" stands for the motor is jammed while rotating |
| battery      | Integer    | the current battery level, `0-100`                                                                                                                                                                              |
| timeOfSample | Long       | the time stamp when the event is sent                                                                                                                                                                           |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoLockProWifi",
        "deviceMac": DEVICE_MAC_ADDR,
        "lockState": "LOCKED",
        "battery": 90,
        "timeOfSample": 123456789
    }
}
```
