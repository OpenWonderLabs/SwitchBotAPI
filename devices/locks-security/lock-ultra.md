# Lock Ultra

---

## Device List Information

| Key                | Value Type      | Description                                                                                       |
| ------------------ | --------------- | ------------------------------------------------------------------------------------------------- |
| deviceId           | String          | device ID                                                                                         |
| deviceName         | String          | device name                                                                                       |
| deviceType         | String          | device type. _Smart Lock Ultra_                                                                   |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device                              |
| hubDeviceId        | String          | device's parent Hub ID                                                                            |
| group              | Boolean         | determines if a Lock is grouped with another Lock or not                                          |
| master             | Boolean         | determines if a Lock is the master device or not when grouped with another Lock in Dual Lock mode |
| groupName          | String          | the name of the Lock group                                                                        |
| lockDevicesIds     | Array<deviceId> | a list of Lock device IDs such that the Lock devices are being grouped in Dual Lock mode          |

---

## Device Status

| Key         | Value Type | Description                                                |
| ----------- | ---------- | ---------------------------------------------------------- |
| deviceId    | String     | device ID                                                  |
| deviceType  | String     | device type. _Lock Ultra_                                  |
| hubDeviceId | String     | device's parent Hub ID                                     |
| battery     | Integer    | the current battery level, 0-100              |
| version     | String     | the current firmware version, e.g. V6.3       |
| lockState   | String     | jammed, unlock, lock, latchBoltLocked         |
| doorState   | String     | open, close                                   |
| calibrate   | Boolean    | determines if Lock has been calibrated or not |

---

## Control Commands

| deviceType | commandType | Command  | command parameter | Description                 |
| ---------- | ----------- | -------- | ----------------- | --------------------------- |
| Lock Ultra | command     | lock     | default           | rotate to locked position   |
| Lock Ultra | command     | unlock   | default           | rotate to unlocked position |
| Lock Ultra | command     | deadbolt | default           | disengage deadbolt or latch |

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
| battery      | Integer    | the battery level                                                                                                                                                                                               |
| timeOfSample | Long       | the time stamp when the event is sent                                                                                                                                                                           |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Smart Lock Ultra",
        "deviceMac": DEVICE_MAC_ADDR,
        "lockState": "LOCKED",
        "battery": 90,
        "timeOfSample": 123456789
    }
}
```
