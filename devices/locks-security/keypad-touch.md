# Keypad Touch

---

## Device List Information

| Key                | Value Type | Description                                                          |
| ------------------ | ---------- | -------------------------------------------------------------------- |
| deviceId           | String     | device ID                                                            |
| deviceName         | String     | device name                                                          |
| deviceType         | String     | device type. _Keypad Touch_                                          |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                               |
| lockDeviceId       | String     | MAC address of the Lock that the current device is paired with       |
| keyList            | Object     | a list of passcodes                                                  |

`keyList` maintains a list of passcodes,

| Key        | Value Type | Description                                                                                                                                                     |
| ---------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id         | Integer    | passcode ID                                                                                                                                                     |
| name       | String     | name of the passcode                                                                                                                                            |
| type       | String     | type of the passcode. _permanent_, a permanent passcode. _timeLimit_, a temporary passcode. _disposable_, a one-time passcode. _urgent_, an emergency passcode. |
| password   | String     | the passcode string encrypted with the developer secret key using the aes-128-cbc algorithm                                                                     |
| iv         | String     | an arbitrary number used for the encryption                                                                                                                     |
| status     | String     | validity of the passcode. _normal_, the passcode is valid. _expired_, the passcode is invalid.                                                                  |
| createTime | Long       | the time when the passcode is generated                                                                                                                         |

---

## Device Status

| Key         | Value Type | Description                 |
| ----------- | ---------- | --------------------------- |
| deviceId    | String     | device ID                   |
| deviceType  | String     | device type. _Keypad Touch_ |
| hubDeviceId | String     | device's parent Hub ID      |

---

## Control Commands

The control commands for this product work differently than the other products. Due to security concerns, the passcodes are stored locally. This mechanism dramatically prolongs the time needed to successfully create a passcode and get the correct result through the Web API. Hence, the actual results of the following commands are returned from the SwitchBot server asynchronously and are delivered through a webhook.

You need to configure a webhook to receive the correct result. Refer to this product's webhook definition.

| deviceType   | commandType | Command   | command parameter                                                                                                                            | Description                 |
| ------------ | ----------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------- |
| Keypad Touch | command     | createKey | { "name": passcode \_name_str, "type": passcode_type_str, "password": passcode_str, "startTime": valid_from_long, "endTime": valid_to_long } | create a new passcode       |
| Keypad Touch | command     | deleteKey | { "id": passcode_id_int }                                                                                                                    | delete an existing passcode |

The following table describes the parameter object for `createKey`,
| Key Name | Value Type | Description |
| ------------ | ---------- | ---------------------------------------------------- |
| name | String | a unique name for the passcode. duplicates under the same device are not allowed. |
| type |String | type of the passcode. _permanent_, a permanent passcode. _timeLimit_, a temporary passcode. _disposable_, a one-time passcode. _urgent_, an emergency passcode. |
| password | String | a 6 to 12-digit passcode in plain text |
| startTime | Long |set the time the passcode becomes valid from, mandatory for one-time passcode and temporary passcode. a 10-digit timestamp.|
| endTime | Long |set the time the passcode becomes expired, mandatory for one-time passcode and temporary passcode. a 10-digit timestamp.|

The following table describes the parameter object for `deleteKey`,
| Key Name | Value Type | Description |
| ------------ | ---------- | ---------------------------------------------------- |
| id | String | the id of the passcode |

---

## Webhook Events

| Key Name     | Value Type | Description                                                                                                                  |
| ------------ | ---------- | ---------------------------------------------------------------------------------------------------------------------------- |
| eventType    | String     | the type of events                                                                                                           |
| eventVersion | String     | the current event version                                                                                                    |
| context      | Object     | the detail info of the event                                                                                                 |
| deviceType   | String     | attributes of the context object. the type of the device                                                                     |
| deviceMac    | String     | attributes of the context object. the MAC address of the device                                                              |
| eventName    | String     | attributes of the context object. the name of the command being sent                                                         |
| commandId    | String     | attributes of the context object. the command id                                                                             |
| result       | String     | attributes of the context object. the result of the command. _success_, _failed_, or _timeout_. timeout duration is 1 minute |
| timeOfSample | Long       | attributes of the context object. the time stamp when the event is sent                                                      |

##### Create a passcode

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoKeypadTouch",
        "deviceMac": DEVICE_MAC_ADDR,
        "eventName": "createKey",
        "commandId": "CMD-1663558451952-01",
        "result": "success",
        "timeOfSample": 123456789
    }
}
```

##### Delete a passcode

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoKeypadTouch",
        "deviceMac": DEVICE_MAC_ADDR,
        "eventName": "deleteKey ",
        "commandId": "CMD-1663558451952-01",
        "result": "success",
        "timeOfSample": 123456789
    }
}
```
