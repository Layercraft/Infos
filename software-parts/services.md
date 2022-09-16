# Services
Diffrent Services in Layercraft

## Game Services

| Chat       | Entity          | World        | Player                    | Server               |
|------------|-----------------|--------------|---------------------------|----------------------|
| Commands   | Entity-Move     | Place-Blocks | Player-Interact           | General Server Stuff |
| Chat       | Entity-Interact | Break-Blocks | Player-Move               |                      |
| Tablist    |                 |              | Inventory / Health / Food |                      |
| Scoreboard |                 |              |                           |                      |

<br>

### Chat Service
+ pub / sub to connector and api client
+ is responsible for everything with the chat in minecraft, so: chat, tablist, scoreboard, commands etc.

### Entity Service
+ pub / sub to tra and api client
+ is responsible for everything with the entities in minecraft, so: entities, spawners, mobs, etc.

### World Service
+ pub / sub to connector and api client
+ is responsible for everything with the world in minecraft, so: world, weather, time, blocks etc.

### Server Service
+ pub / sub to connector and api client
+ simulate the diffrent instances of the server

### Player Service
+ pub / sub to connector and api client
+ is responsible for everything with the players in minecraft, so: players, health, inventory, etc.

## Session Service
+ communicate with the connector and api client
+ communicate with the mojang session service or a own session service
+ makes the entire login process from the client to the server
