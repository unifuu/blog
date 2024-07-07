---
title: "Memo of MongoDB"
date: 2024-07-02
tags: ["MongoDB"]
---

## Command

``` sh
sudo docker exec -it 103 bash

# Open the MongoDB shell
mongosh

# Switch to the database
use ditto

# Drop the database
db.dropDatabase()

# Copy the backup of the database to Docker
sudo docker cp 202405 103:/202405

# Restore the database
sudo docker exec -i 103 /usr/bin/mongorestore --db ditto /202405/ditto

# Rename a field
db.[COLLECTION].updateMany({}, { $rename: { ["OLD"]: ["NEW"] } })
```

## Memo

### Temp

``` sh
db.game.updateMany({}, { $rename: { "total_time": "played_time" } })
db.game.updateMany({}, { $rename: { "developer_id": "developer" } })
db.game.updateMany({}, { $rename: { "publisher_id": "publisher" } })
db.game.updateMany({}, { $rename: { "how_long_to_beat": "time_to_beat" } })
```
