- Start Date: 2021-07-03
- Target Major Version: 1.x
- Reference Issues: (leave this empty)
- Implementation PR: (leave this empty)

# Milvus interface

## collection
- create collection
- describe collection
- delete collection
- list collections ***with pagination***

### collection index
- create collection index
- describe collection index
- delete collection index
- get collection index
- get create index status

## partition
- create partition
- describe partition
- delete partition
- list partitions ***with pagination***

## entities
- list entities in a partition ***with pagination***
- get entities count in a collection
- get entities count in a partition

## search
- get loaded collections
- vector search on a loaded collection

## system
- get system configuration
- get system topology
- get system node information
  - query/data/index node info
    - node count
    - node name
    - node address
    - node status
    - cpu
    - memory usage
- get system statistics
  - total entities count
  - total storage usage and 
    - index file storage usage
    - entities storage usage
    - logs storage usage


