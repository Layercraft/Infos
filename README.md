# Infos
> Infos about the project.

The goal is to develop a new Minecraft server according to modern standards. This means stateless design pattern and a implementation which should go in the direction of reactive microservices.

### Infos about the *fancy* keywords:

- [Microservices](https://en.wikipedia.org/wiki/Microservices)
- [SOA](https://en.wikipedia.org/wiki/Service-oriented_architecture)
- [Reactive](https://en.wikipedia.org/wiki/Reactive_programming)
- [Reactive Microservices](https://www.lightbend.com/microservices/reactive-microservices-events-domain-driven-design-ddd)
- [Stateless](https://en.wikipedia.org/wiki/Service_statelessness_principle)

### Microservices trade-offs
The Notchain Minecraft server is not microservice or stateless, so the Minecraft client is not designed that way. That's why we have to mix SOA and microservices. 

### Stateless
Important: Everything runs stateless. Only the database knows.

### Plugins
Problems with a decentralized minecraft server but a central plugin and our way around it:
It is a small paradox to pull something apart only to make it centrally accessible again at the end. We have thought about this problem a lot and got stuck with our current solution. We don't have a direct connection between api, translator or mc services, this will only work through a message service, we do this to continue the concept of asynchrony and not to introduce a complex system between client and server communication. 


## Goals:
+ better performance usage as the normal minecraft server
+ better security, though security filtering in the first place
+ handle more players with less hardware, becuase of better scaling from different services
+ more features, through better api architecture, like minestom
+ able to handle hunderts or thousands players on the same world
+ (easy) k8s deployment :)

Baisc idea for the technical stack:
[TECHSTACK](./TECHSTACK.md)


## Overview:
![Overview](images/overview.png)

Explaning the diffrent parts of the system:

- Connector: Here will the minecraft client connect to the server. And translates the packet from java or bedrock to a universal format. And send it into the message service.
- Message Service: The message service is the central point of the system. It will handle the communication between the api, the connector and the mc services.
- MC Services: On the mc services runs all important stuff like the world, the player, the inventory, the crafting, the chat, the command etc. for a actual minecraft server. Most things in a event driven way.
- API: The api is the interface between the services and the *plugins*.

More Explaning: 
- [API](./software-parts/api.md)
- [Services](./software-parts/services.md)
- [Connector](./software-parts/connector.md)
