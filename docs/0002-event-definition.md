- Start Date: 2021-07-03
- Target Major Version: 1.x
- Reference Issues: (leave this empty)
- Implementation PR: (leave this empty)

# Milvus events
## Basic description
The Milvus system generates events, such as informational events and error events. 
- You can use the object code to determine the type of the object the event is logged against.
- An object ID or number is the unique identifier of the target object.
- An event ID or number is associated with the event and indicates the reason for the event.
- Informational events provide information about the status of an operation.  
- Error events are generated when a service action is required. An error event maps to an alert with an associated error code.

### Object Types

| Object code | Object Type |
| :---------: | :---------- |
|      0      | system      |
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


### Events types
Informational events can be either notification type I (information) or notification type W (warning). An informational event report of type (W) might require user attention. Error codes can be either notification type E (error) or notification type W (warning).

| Notification type | Description |
| :---------------: | :---------- |
|         I         | information |
|         W         | warning     |
|         E         | error       |

## Events details

### system
| Object code | Object ID | Event ID | Notification type | Description                       | Error Code |
| :---------: | :-------: | :------: | :---------------- | :-------------------------------- | :--------- |
|      0      |    001    |  000004  | E                 | CPU is not compatible with milvus | 000001     |

### collection
| Object code | Object ID | Event ID | Notification type | Description         | Error Code |
| :---------: | :-------: | :------: | :---------------- | :------------------ | :--------- |
|      1      |    123    |  000001  | I                 | collection created  |            |
|      1      |    123    |  000002  | I                 | collection renamed  |            |
|      1      |    123    |  000003  | I                 | collection deleted  |            |
|      1      |    123    |  000004  | I                 | collection loaded   |            |
|      1      |    123    |  000005  | I                 | collection released |            |

### partition
| Object code | Object ID | Event ID | Notification type | Description        | Error Code |
| :---------: | :-------: | :------: | :---------------- | :----------------- | :--------- |
|      2      |    123    |  000001  | I                 | partition created  |            |
|      2      |    123    |  000002  | I                 | partition renamed  |            |
|      2      |    123    |  000003  | I                 | partition deleted  |            |
|      2      |    123    |  000004  | I                 | partition loaded   |            |
|      2      |    123    |  000005  | I                 | partition released |            |

### index
| Object code | Object ID | Event ID | Notification type | Description    | Error Code |
| :---------: | :-------: | :------: | :---------------- | :------------- | :--------- |
|      3      |    123    |  000001  | I                 | index created  |            |
|      3      |    123    |  000002  | I                 | index renamed  |            |
|      3      |    123    |  000003  | I                 | index deleted  |            |
|      3      |    123    |  000004  | I                 | index loaded   |            |
|      3      |    123    |  000005  | I                 | index released |            |


### rootCoord
| Object code | Object ID | Event ID | Notification type | Description                      | Error Code |
| :---------: | :-------: | :------: | :---------------- | :------------------------------- | :--------- |
|     100     |    001    |  000001  | I                 | root coord is online             |            |
|     100     |    001    |  000004  | I                 | root coord is offline            |            |
|     100     |    001    |  000004  | I                 | TSC error                        | 040000     |
|     100     |    001    |  000004  | E                 | unable to connect to data broker | 040000     |
|     100     |    001    |  000004  | E                 | unable to connect to query coord | 040000     |
|     100     |    001    |  000004  | E                 | unable to connect to index coord | 040000     |
|     100     |    001    |  000004  | E                 | unable to connect to data coord  | 040000     |

### proxy
| Object code | Object ID | Event ID | Notification type | Description                      | Error Code |
| :---------: | :-------: | :------: | :---------------- | :------------------------------- | :--------- |
|     101     |    001    |  000002  | I                 | proxy is offline                 |            |
|     101     |    001    |  000004  | I                 | proxy is offline                 |            |
|     101     |    001    |  000004  | E                 | unable to connect to data broker | 040000     |
|     101     |    001    |  000004  | E                 | unable to connect to query coord | 040000     |
|     101     |    001    |  000004  | E                 | unable to connect to index coord | 040000     |
|     101     |    001    |  000004  | E                 | unable to connect to data coord  | 040000     |

### query coord
| Object code | Object ID | Event ID | Notification type | Description            | Error Code |
| :---------: | :-------: | :------: | :---------------- | :--------------------- | :--------- |
|     102     |    001    |  000002  | I                 | query coord is offline |            |
|     102     |    001    |  000004  | E                 | query coord is offline | 000001     |

### query node
| Object code | Object ID | Event ID | Notification type | Description              | Error Code |
| :---------: | :-------: | :------: | :---------------- | :----------------------- | :--------- |
|     103     |    001    |  000004  | I                 | query node is online     |            |
|     103     |    001    |  000004  | E                 | query node is offline    | 000001     |
|     103     |    001    |  000004  | W                 | cpu is too busy          | 000002     |
|     103     |    001    |  000004  | W                 | memory usage is too high | 101010     |

### index coord
| Object code | Object ID | Event ID | Notification type | Description            | Error Code |
| :---------: | :-------: | :------: | :---------------- | :--------------------- | :--------- |
|     104     |    001    |  000002  | I                 | index coord is offline |            |
|     104     |    001    |  000004  | E                 | index coord is offline |            |


### index node
| Object code | Object ID | Event ID | Notification type | Description              | Error Code |
| :---------: | :-------: | :------: | :---------------- | :----------------------- | :--------- |
|     105     |    001    |  000004  | I                 | index node is online     |            |
|     105     |    001    |  000004  | E                 | index node is offline    | 000001     |
|     105     |    001    |  000004  | W                 | cpu is too busy          | 000002     |
|     105     |    001    |  000004  | W                 | memory usage is too high | 000001     |


### data coord
| Object code | Object ID | Event ID | Notification type | Description           | Error Code |
| :---------: | :-------: | :------: | :---------------- | :-------------------- | :--------- |
|     106     |    001    |  000002  | I                 | data coord is offline |            |
|     106     |    001    |  000004  | I                 | data coord is offline |            |


### data node
| Object code | Object ID | Event ID | Notification type | Description              | Error Code |
| :---------: | :-------: | :------: | :---------------- | :----------------------- | :--------- |
|     107     |    001    |  000004  | I                 | data node is online      |            |
|     107     |    001    |  000004  | E                 | data node is offline     | 000001     |
|     107     |    001    |  000004  | W                 | cpu is too busy          | 000002     |
|     107     |    001    |  000004  | W                 | memory usage is too high | 000001     |

### meta storage
| Object code | Object ID | Event ID | Notification type | Description             | Error Code |
| :---------: | :-------: | :------: | :---------------- | :---------------------- | :--------- |
|     108     |    001    |  000004  | I                 | meta storage is online  |            |
|     108     |    001    |  000004  | I                 | meta storage is offline |            |
|     108     |    001    |  000004  | E                 | meta storage is full    | 000003     |

### log broker
| Object code | Object ID | Event ID | Notification type | Description           | Error Code |
| :---------: | :-------: | :------: | :---------------- | :-------------------- | :--------- |
|     109     |    001    |  000004  | I                 | log broker is online  |            |
|     109     |    001    |  000004  | I                 | log broker is offline |            |
|     109     |    001    |  000004  | E                 | log broker is full    | 000003     |

### Object storage
| Object code | Object ID | Event ID | Notification type | Description               | Error Code |
| :---------: | :-------: | :------: | :---------------- | :------------------------ | :--------- |
|     110     |    001    |  000004  | I                 | object storage is online  |            |
|     110     |    001    |  000004  | I                 | object storage is offline |            |
|     110     |    001    |  000004  | E                 | object storage is full    | 000003     |