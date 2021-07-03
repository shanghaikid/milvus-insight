- Start Date: 2021-07-03
- Target Major Version: 1.x
- Reference Issues: (leave this empty)
- Implementation PR: (leave this empty)

# Summary
Introducing a new API server communication method among the milvus cluster, the Milvus insight API server, and the frontend:
The API server will talk to the milvus cluster with SDKs regularly, and store everything in the cache layer, and send updates to the browser via websocket.
it contains:
- a cache layer for the persistent of milvus objects.
- an event system which will send the system changes to the clients.
- a websocket server which could be used to communicate between the server and the client.
- a cron job which keep updating the cache layer.

## Why we need this layer?
From GUI perspective, user needs to list/search colleciton/partiton or other meta objects, currently we retrieve all objects in one time, and do the search at the browser side, it will soon become unusage with the increasing objects count, so we need do all these actions in the backend.

# Rough design
## Data flow
1. Start the API server and connect to the Milvus cluster
2. API server should
  - Find if the cache layer exists, if not create it.
3. API sever start the cron job which keeps updating data to the cache layer.
4. User disconnects to the Milvus cluster, the API server should 
  - stop and save everything to the cache layer
  - stop the cron job
5. Waiting for new connection.
## The cache layer
The cache layer is per server address per layer. If user connects to different cluster, we need to create different cache layer. There are two choices about the cache layer: 
#### In memory db
- [pouchdb](https://pouchdb.com/)
- [lokijs](https://github.com/techfort/LokiJS)
#### nosql db
- [mongodb](https://www.mongodb.com/)
- [rethinkdb](https://rethinkdb.com/)
- [couchdb](https://couchdb.apache.org/)

In the currently stage, I prefer in js memory db, we don't need to store states right now. 

### Event system implementation
- if the layer cache has its event system, we can use it, otherwise it is not really difficult to implement our own one. 
### WebSocket system implementation
- [nestjs ws docs](https://docs.nestjs.com/websockets/gateways)
### cron job
- [nestjs scheduling docs](https://docs.nestjs.com/techniques/task-scheduling)

## Event definition
We may need to discuss this with milvus team.

# Drawbacks
- It doesn't store states, if user restart milvus insight, all the cache will be gone. 
- A little bit complicated to implement, both the client and API server needs to change. 
