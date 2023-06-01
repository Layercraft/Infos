# Services
Diffrent Services in Layercraft

## Game Services

| Chat       | Entity          | World        | Player                    | Instance             |
|------------|-----------------|--------------|---------------------------|----------------------|
| Commands   | Entity-Move     | Place-Blocks | Player-Interact           | General Server Stuff |
| Chat       | Entity-Interact | Break-Blocks | Player-Move               |                      |
| Tablist    |                 |              | Inventory / Health / Food |                      |
| Scoreboard |                 |              |                           |                      |

<br>

### Chat Service
+ pub / sub to connector and api client
+ is responsible for everything with the chat in minecraft, so: chat, tablist, scoreboard, commands etc.
+ works completly event driven

### Entity Service
+ pub / sub to connector and api client
+ is responsible for everything with the entities in minecraft, so: entities, spawners, mobs, etc.
+ works completly event driven and have is own task system e.g. for entity movement
+ maybe split into more services, like: entity, entity-movement, entity-interact, etc.

### World Service
+ pub / sub to connector and api client
+ is responsible for everything with the world in minecraft, so: world, weather, time, blocks etc.
+ works completly event driven and have is own task system e.g. for redstone and block updates(like water, lava, etc.)
+ Cache read only worlds in redis or/and in service?
+ 3 diffrent world types: only read: lobby, only a read, no block update exist; read-only with write: bedwars, existing map where only the changes are written to the database; read and write: vanilla, where the whole world is written to the database, every chunk is a row and every block form that chunk is a column
+ maybe split into more services, like: world, weather, time, blocks, etc.


### Instance Service
+ pub / sub to connector and api client
+ start and stop the instance, plugin management, graphql api, etc.
+ graphql api for the instance


### Player Service
+ pub / sub to connector and api client
+ is responsible for everything with the players in minecraft, so: players, health, inventory, etc.
+ works completly event driven and have is own task system e.g. for player movement
+ maybe split into more services, like: player, player-movement, player-interact, etc.
