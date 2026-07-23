# AI MindClip

---

## Device List Information

| Key        | Value Type | Description                       |
| ---------- | ---------- | --------------------------------- |
| deviceId   | String     | device ID                         |
| deviceName | String     | device name                       |
| deviceType | String     | device type. _AI MindClip_        |

---

## Device Status

| Key                   | Value Type | Description                                                    |
| --------------------- | ---------- | -------------------------------------------------------------- |
| deviceId              | String     | device ID                                                      |
| deviceType            | String     | device type. _AI MindClip_                                     |
| battery               | Integer    | the current battery level, 0-100                               |
| chargingStatus        | Integer    | charge state. `0`, uncharged; `1`, charging                    |
| recordingStatus       | Integer    | recording state. `0`, not recording; `1`, recording            |
| uploadStatus          | Integer    | upload state. `0`, not uploaded; `1`, uploading                |
| hasUntransferredFiles | Boolean    | determines if the device has files that are not transferred    |

---

## Control Commands

AI MindClip does not support device control commands.

---

## Feature APIs

### Get recording list

```http
GET /v1.1/mindclip/recordings?deviceID={deviceID}&pageNum={pageNum}&pageSize={pageSize}
```

**Available for:** SwitchBot AI MindClip

#### Description

Gets a paginated list of recordings created by an AI MindClip device.

#### Query parameters

| Parameter | Type    | Required | Description |
| --------- | ------- | -------- | ----------- |
| deviceID  | String  | Yes      | device ID |
| pageNum   | Integer | Yes      | page number |
| pageSize  | Integer | Yes      | number of recordings returned per page |

#### Response

The `body` object contains the following properties,

| Key Name                | Value Type | Description |
| ----------------------- | ---------- | ----------- |
| total                   | Integer    | total number of recordings |
| pageNum                 | Integer    | current page number |
| pageSize                | Integer    | number of recordings returned per page |
| pages                   | Integer    | total number of pages |
| list                    | Array      | recording list |
| list[].id               | String     | recording ID |
| list[].displayName      | String     | recording display name |
| list[].recordingLen     | Integer    | recording length |
| list[].fileSize         | Integer    | recording file size |
| list[].deviceID         | String     | device ID |
| list[].transcribeStatus | Integer    | transcription status |
| list[].createdTime      | Integer    | created time in Unix milliseconds |
| list[].folderID         | Integer    | folder ID |
| list[].emoji            | String     | folder or recording emoji |
| list[].isSystem         | Boolean    | determines if the folder is a system folder |

```json
{
    "statusCode": 100,
    "message": "success",
    "body": {
        "total": 1,
        "pageNum": 1,
        "pageSize": 20,
        "pages": 1,
        "list": [
            {
                "id": "5f3a1c2e9b7d",
                "displayName": "Team sync",
                "recordingLen": 1820,
                "fileSize": 2931456,
                "deviceID": "AABBCCDDEEFF",
                "transcribeStatus": 2,
                "createdTime": 1716000000000,
                "folderID": 3,
                "emoji": "📁",
                "isSystem": false
            }
        ]
    }
}
```

#### Error codes

Refer to [Standard HTTP Error Codes](../../README.md#standard-http-error-codes) for error handling.

#### Sample request

```http
GET /v1.1/mindclip/recordings?deviceID=AABBCCDDEEFF&pageNum=1&pageSize=20 HTTP/1.1
Host: api.switch-bot.com
Authorization: <token>
sign: <signature>
nonce: <nonce>
t: <timestamp>
```

### Get recording detail

```http
GET /v1.1/mindclip/recordings/{recordingId}
```

**Available for:** SwitchBot AI MindClip

#### Description

Gets the metadata for a specified AI MindClip recording.

#### Path parameters

| Parameter   | Type   | Required | Description |
| ----------- | ------ | -------- | ----------- |
| recordingId | String | Yes      | recording ID |

#### Response

The `body` object contains the following properties,

| Key Name         | Value Type | Description |
| ---------------- | ---------- | ----------- |
| id               | String     | recording ID |
| displayName      | String     | recording display name |
| recordingLen     | Integer    | recording length |
| fileSize         | Integer    | recording file size |
| deviceID         | String     | device ID |
| transcribeStatus | Integer    | transcription status |
| createdTime      | Integer    | created time in Unix milliseconds |
| folderID         | Integer    | folder ID |
| emoji            | String     | folder or recording emoji |
| isSystem         | Boolean    | determines if the folder is a system folder |

```json
{
    "statusCode": 100,
    "message": "success",
    "body": {
        "id": "5f3a1c2e9b7d",
        "displayName": "Team sync",
        "recordingLen": 1820,
        "fileSize": 2931456,
        "deviceID": "AABBCCDDEEFF",
        "transcribeStatus": 2,
        "createdTime": 1780060800000,
        "folderID": 3,
        "emoji": "note",
        "isSystem": false
    }
}
```

#### Error codes

Refer to [Standard HTTP Error Codes](../../README.md#standard-http-error-codes) for error handling.

#### Sample request

```http
GET /v1.1/mindclip/recordings/5f3a1c2e9b7d HTTP/1.1
Host: api.switch-bot.com
Authorization: <token>
sign: <signature>
nonce: <nonce>
t: <timestamp>
```

### Get recording summary

```http
GET /v1.1/mindclip/summaries/{recordingId}
```

**Available for:** SwitchBot AI MindClip

#### Description

Gets the transcript, AI summary, template result, atmosphere analysis, extracted todos, and speaker information for a specified recording.

#### Path parameters

| Parameter   | Type   | Required | Description |
| ----------- | ------ | -------- | ----------- |
| recordingId | String | Yes      | recording ID |

#### Response

The `body` object contains the following properties,

| Key Name         | Value Type | Description |
| ---------------- | ---------- | ----------- |
| fileID           | String     | recording file ID |
| transcribeStatus | Integer    | transcription status |
| transcribeResult | String     | transcript text |
| aiSummaryResult  | String     | AI summary text |
| aiTemplateResult | String     | AI template result |
| aiAtmoResult     | String     | AI atmosphere result |
| aiTodoList       | Array      | AI extracted todo items |
| aiTodoList[].title | String   | todo title |
| aiTodoList[].reminderTime | Integer | reminder time in Unix milliseconds |
| aiTodoList[].isCompleted | Boolean | determines if the todo is completed |
| aiTodoList[].createdTime | Integer | created time in Unix milliseconds |
| aiTodoList[].fileID | String   | recording file ID |
| aiTodoList[].deviceID | String | device ID |
| aiTodoList[].category | Integer | todo category |
| speakers         | Array      | speaker information |
| speakers[].speaker | String   | speaker identifier |
| speakers[].speakerName | String | speaker name |
| speakers[].lightColor | String | speaker color for light mode |
| speakers[].darkColor | String | speaker color for dark mode |
| speakers[].speakerConfidence | Number | speaker recognition confidence |

```json
{
    "statusCode": 100,
    "message": "success",
    "body": {
        "fileID": "5f3a1c2e9b7d",
        "transcribeStatus": 2,
        "transcribeResult": "Alice: Let's review the release plan.",
        "aiSummaryResult": "Key decisions: ship v2 next week.",
        "aiTemplateResult": "## Meeting Notes\n- Ship v2 next week",
        "aiAtmoResult": "Focused and collaborative",
        "aiTodoList": [
            {
                "title": "Send meeting notes to team",
                "reminderTime": 1780147200000,
                "isCompleted": false,
                "createdTime": 1780060800000,
                "fileID": "5f3a1c2e9b7d",
                "deviceID": "AABBCCDDEEFF",
                "category": 1
            }
        ],
        "speakers": [
            {
                "speaker": "spk_1",
                "speakerName": "Alice",
                "lightColor": "#FFB300",
                "darkColor": "#FFD54F",
                "speakerConfidence": 0.92
            }
        ]
    }
}
```

#### Error codes

Refer to [Standard HTTP Error Codes](../../README.md#standard-http-error-codes) for error handling.

#### Sample request

```http
GET /v1.1/mindclip/summaries/5f3a1c2e9b7d HTTP/1.1
Host: api.switch-bot.com
Authorization: <token>
sign: <signature>
nonce: <nonce>
t: <timestamp>
```

### Get todo list

```http
GET /v1.1/mindclip/todos?completedNum={completedNum}&pageNum={pageNum}&pageSize={pageSize}
```

**Available for:** SwitchBot AI MindClip

#### Description

Gets a paginated list of todos extracted from AI MindClip recordings.

#### Query parameters

| Parameter    | Type    | Required | Description |
| ------------ | ------- | -------- | ----------- |
| completedNum | Integer | Yes      | completion-state filter |
| pageNum      | Integer | Yes      | page number |
| pageSize     | Integer | Yes      | number of todos returned per page |

#### Response

The `body` object contains the following properties,

| Key Name               | Value Type | Description |
| ---------------------- | ---------- | ----------- |
| total                  | Integer    | total number of todos |
| pageNum                | Integer    | current page number |
| pageSize               | Integer    | number of todos returned per page |
| pages                  | Integer    | total number of pages |
| list                   | Array      | todo list |
| list[].title           | String     | todo title |
| list[].reminderTime    | Integer    | reminder time in Unix milliseconds |
| list[].isCompleted     | Boolean    | determines if the todo is completed |
| list[].createdTime     | Integer    | created time in Unix milliseconds |
| list[].fileID          | String     | recording file ID |
| list[].deviceID        | String     | device ID |
| list[].category        | Integer    | todo category |

```json
{
    "statusCode": 100,
    "message": "success",
    "body": {
        "total": 1,
        "pageNum": 1,
        "pageSize": 20,
        "pages": 1,
        "list": [
            {
                "title": "Send meeting notes to team",
                "reminderTime": 1716100000000,
                "isCompleted": false,
                "createdTime": 1716000000000,
                "fileID": "5f3a1c2e9b7d",
                "deviceID": "AABBCCDDEEFF",
                "category": 1
            }
        ]
    }
}
```

#### Error codes

Refer to [Standard HTTP Error Codes](../../README.md#standard-http-error-codes) for error handling.

#### Sample request

```http
GET /v1.1/mindclip/todos?completedNum=0&pageNum=1&pageSize=20 HTTP/1.1
Host: api.switch-bot.com
Authorization: <token>
sign: <signature>
nonce: <nonce>
t: <timestamp>
```

### Get daily memory

```http
GET /v1.1/mindclip/assistant/daily?date={date}
```

**Available for:** SwitchBot AI MindClip

#### Description

Gets the AI MindClip daily memory for a specified date.

#### Query parameters

| Parameter | Type   | Required | Description |
| --------- | ------ | -------- | ----------- |
| date      | String | Yes      | date in `YYYY-MM-DD` format |

#### Response

The `body` object contains the following properties,

| Key Name                    | Value Type | Description |
| --------------------------- | ---------- | ----------- |
| list                        | Array      | daily memory records |
| list[].summaryDate          | String     | summary date in `YYYY-MM-DD` format |
| list[].summaryContent       | String     | daily summary content |
| list[].status               | Integer    | summary generation status |
| list[].timezone             | String     | timezone |
| list[].locations            | Array      | locations associated with the daily memory |
| list[].locations[].timestamp | Integer   | location time in Unix seconds |
| list[].locations[].latitude | Number     | latitude |
| list[].locations[].longitude | Number    | longitude |
| list[].locations[].placeName | String    | place name |
| list[].locations[].fileID   | String     | related recording file ID |

```json
{
    "statusCode": 100,
    "message": "success",
    "body": {
        "list": [
            {
                "summaryDate": "2026-05-30",
                "summaryContent": "Today you had 3 meetings and created 2 todos.",
                "status": 1,
                "timezone": "Asia/Shanghai",
                "locations": [
                    {
                        "timestamp": 1780060800,
                        "latitude": 31.23,
                        "longitude": 121.47,
                        "placeName": "Shanghai Office",
                        "fileID": "5f3a1c2e9b7d"
                    }
                ]
            }
        ]
    }
}
```

#### Error codes

Refer to [Standard HTTP Error Codes](../../README.md#standard-http-error-codes) for error handling.

#### Sample request

```http
GET /v1.1/mindclip/assistant/daily?date=2026-05-30 HTTP/1.1
Host: api.switch-bot.com
Authorization: <token>
sign: <signature>
nonce: <nonce>
t: <timestamp>
```

### Get weekly summary

```http
GET /v1.1/mindclip/assistant/weekly?week={week}
```

**Available for:** SwitchBot AI MindClip

#### Description

Gets the AI MindClip weekly summary for a specified ISO week.

#### Query parameters

| Parameter | Type   | Required | Description |
| --------- | ------ | -------- | ----------- |
| week      | String | Yes      | ISO week in `YYYY-Www` format |

#### Response

The `body` object contains the following properties,

| Key Name        | Value Type | Description |
| --------------- | ---------- | ----------- |
| summaryWeek     | String     | ISO week in `YYYY-Www` format |
| summaryContent  | String     | weekly summary content |
| status          | Integer    | summary generation status |
| timezone        | String     | timezone |

```json
{
    "statusCode": 100,
    "message": "success",
    "body": {
        "summaryWeek": "2026-W22",
        "summaryContent": "This week you recorded 12 sessions across 5 days.",
        "status": 1,
        "timezone": "Asia/Shanghai"
    }
}
```

#### Error codes

Refer to [Standard HTTP Error Codes](../../README.md#standard-http-error-codes) for error handling.

#### Sample request

```http
GET /v1.1/mindclip/assistant/weekly?week=2026-W22 HTTP/1.1
Host: api.switch-bot.com
Authorization: <token>
sign: <signature>
nonce: <nonce>
t: <timestamp>
```

### Get urgent todo list

```http
GET /v1.1/mindclip/assistant/urgent-todos?date={date}
```

**Available for:** SwitchBot AI MindClip

#### Description

Gets urgent AI MindClip todos for a specified date.

#### Query parameters

| Parameter | Type   | Required | Description |
| --------- | ------ | -------- | ----------- |
| date      | String | Yes      | date in `YYYY-MM-DD` format |

#### Response

The `body` object contains the following properties,

| Key Name              | Value Type | Description |
| --------------------- | ---------- | ----------- |
| summaryDate           | String     | summary date in `YYYY-MM-DD` format |
| todos                 | Array      | urgent todo items |
| todos[].title         | String     | todo title |
| todos[].reminderTime  | Integer    | reminder time in Unix milliseconds |
| todos[].rank          | Integer    | todo priority rank |
| todos[].fileID        | String     | related recording file ID |
| todos[].isCompleted   | Boolean    | determines if the todo is completed |
| todos[].category      | Integer    | todo category |

```json
{
    "statusCode": 100,
    "message": "success",
    "body": {
        "summaryDate": "2026-05-30",
        "todos": [
            {
                "title": "Send meeting notes to team",
                "reminderTime": 1780147200000,
                "rank": 1,
                "fileID": "5f3a1c2e9b7d",
                "isCompleted": false,
                "category": 1
            }
        ]
    }
}
```

#### Error codes

Refer to [Standard HTTP Error Codes](../../README.md#standard-http-error-codes) for error handling.

#### Sample request

```http
GET /v1.1/mindclip/assistant/urgent-todos?date=2026-05-30 HTTP/1.1
Host: api.switch-bot.com
Authorization: <token>
sign: <signature>
nonce: <nonce>
t: <timestamp>
```

---

## Webhook Events

| Key Name                        | Value Type | Description                                                                                                                     |
| ------------------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------- |
| eventType                       | String     | the type of events                                                                                                              |
| eventVersion                    | String     | the current event version                                                                                                       |
| context                         | Object     | the detail info of the event                                                                                                    |
| deviceType                      | String     | the type of the device                                                                                                          |
| deviceMac                       | String     | the MAC address of the device                                                                                                   |
| timeOfSample                    | Long       | the time stamp when the event is sent                                                                                           |
| chargeUploadCompleted           | Object     | charge upload completion event                                                                                                  |
| chargeUploadCompleted.fileID    | String     | recording file ID                                                                                                               |
| chargeUploadCompleted.fileName  | String     | recording file name                                                                                                             |
| chargeUploadCompleted.status    | Integer    | charge upload status. `1`, completed                                                                                            |
| chargeUploadCompleted.timestamp | Long       | charge upload completion timestamp                                                                                              |
| transcription                   | Object     | transcription status event                                                                                                      |
| transcription.fileID            | String     | recording file ID                                                                                                               |
| transcription.status            | Integer    | `0`, not transcribed; `1`, transcribing; `2`, succeeded; `3`, failed; `4`, timed out; `5`, speech transcription failed          |
| transcription.timestamp         | Long       | transcription event timestamp                                                                                                   |
| dailySummary                    | Long       | daily summary generation timestamp                                                                                              |
| weeklySummary                   | Long       | weekly summary generation timestamp                                                                                             |

Charge upload completion example,

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "AI MindClip",
        "deviceMac": "AIPINNOTE-DEVICE-001",
        "timeOfSample": 1749542100000,
        "chargeUploadCompleted": {
            "fileID": "20260610143022001",
            "fileName": "2026-06-10 14:30",
            "status": 1,
            "timestamp": 1749542100000
        }
    }
}
```

Transcription example,

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "AI MindClip",
        "deviceMac": "AIPINNOTE-DEVICE-001",
        "timeOfSample": 1749542400000,
        "transcription": {
            "fileID": "20260610143022001",
            "status": 1,
            "timestamp": 1749542400000
        }
    }
}
```

Daily memory generation example,

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "AI MindClip",
        "deviceMac": "AIPINNOTE-DEVICE-001",
        "timeOfSample": 1749556800000,
        "dailySummary": 1749556800
    }
}
```

Weekly summary generation example,

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "AI MindClip",
        "deviceMac": "AIPINNOTE-DEVICE-001",
        "timeOfSample": 1749816000000,
        "weeklySummary": 1749816000
    }
}
```
