# Lock Vision Pro

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Lock Vision Pro_                                       |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |
| keyList            | Object     | a list of passcodes                                                  |

`keyList` maintains a list of passcodes,

| Key        | Value Type | Description                                                                                                                    |
| ---------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------ |
| id         | Integer    | passcode ID                                                                                                                    |
| name       | String     | name of the passcode                                                                                                           |
| type       | String     | type of the passcode. _permanent_, a permanent passcode. _timeLimit_, a temporary passcode. _disposable_, a one-time passcode. |
| password   | String     | the passcode string encrypted with the developer secret key using the aes-128-cbc algorithm                                    |
| iv         | String     | an arbitrary number used for the encryption                                                                                    |
| status     | String     | validity of the passcode. _normal_, the passcode is valid. _expired_, the passcode is invalid.                                 |
| createTime | Long       | the time when the passcode is generated                                                                                        |

---

## Device Status

| Key          | Value Type | Description                                                |
| ------------ | ---------- | ---------------------------------------------------------- |
| deviceId     | String     | device ID                                                  |
| deviceType   | String     | device type. _Lock Vision Pro_                             |
| hubDeviceId  | String     | device's parent Hub ID                                     |
| battery      | Integer    | the current battery level, 0-100                           |
| version      | String     | the current firmware version, e.g. V6.3                    |
| lockState    | String     | jammed, unlock, lock, latchBoltLocked                      |
| doorState    | String     | open, close                                                |
| calibrate    | Boolean    | determines if Lock has been calibrated or not              |
| onlineStatus | String     | the connection status of the device. _online_ or _offline_ |

---

## Control Commands

| deviceType      | commandType | Command   | command parameter                                               | Description                 |
| --------------- | ----------- | --------- | --------------------------------------------------------------- | --------------------------- |
| Lock Vision Pro | command     | lock      | default                                                         | rotate to locked position   |
| Lock Vision Pro | command     | unlock    | default                                                         | rotate to unlocked position |
| Lock Vision Pro | command     | deleteKey | `{"id": ""}`                                                    | delete a passcode by id     |
| Lock Vision Pro | command     | createKey | `{"name":"","type":"","password":"","startTime":0,"endTime":0}` | create a passcode           |

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
        "deviceType": "W1141001",
        "deviceMac": DEVICE_MAC_ADDR,
        "lockState": "LOCKED",
        "battery": 90,
        "timeOfSample": 123456789
    }
}
```
