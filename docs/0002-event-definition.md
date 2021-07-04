- Start Date: 2021-07-03
- Target Major Version: 1.x
- Reference Issues: (leave this empty)
- Implementation PR: (leave this empty)

## Object Types

You can use the object code to determine the type of the object the event is logged against.

| Object code | Object Type |
| :---------: | :---------- |
|      1      | collection  |
|      2      | partition   |
|      3      | index       |
|     100     | rootCoord   |
|     101     | proxy       |
|     102     | queryCoord  |
|     103     | queryNode   |
|     104     | indexCoord  |
|     105     | indexNode   |
|     106     | dataCoord   |
|     107     | dataNode    |
|     108     | metaStore   |
|     109     | logBroker   |
|     110     | objStorage  |

## Event IDs

The Milvus system generates events, such as informational events and error events. An event ID or number is associated with the event and indicates the reason for the event.

Informational events provide information about the status of an operation. Informational events are recorded in the event log.

Error events are generated when a service action is required. An error event maps to an alert with an associated error code.

## Informational events

Informational events can be either notification type I (information) or notification type W (warning). An informational event report of type (W) might require user attention.

| Event ID | Notification type | Description |
| :------: | :---------------- | :---------- |
|  000001  | I                 | collection  |
|  000002  | I                 | collection  |

## Error codes

Error codes describe a service procedure that must be followed. Each event ID that requires service has an associated error code.

Error codes can be either notification type E (error) or notification type W (warning).

| Event ID | Notification type | Description | Error Code |
| :------: | :---------------- | :---------- | :--------- |
|  000001  | E                 | collection  | collection |
|  000002  | W                 | collection  | collection |
