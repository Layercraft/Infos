# Infos
Infos about the project.

The goal is a new development of the Minecraft server according to new standards and their implementation which should go in the direction of reactive microservices and SOA.

Infos about that:

- [Microservices](https://en.wikipedia.org/wiki/Microservices)
- [SOA] (https://en.wikipedia.org/wiki/Service-oriented_architecture)
- [Reactive] (https://en.wikipedia.org/wiki/Reactive_programming)
- [Reactive Microservices](https://www.lightbend.com/microservices/reactive-microservices-events-domain-driven-design-ddd)


Unfortunatly, the default Minecraft server is not a microservice. It is a monolithic application. Exactly the same as the minecraft client.
So, unfortunately, we have to deviate a bit from the concept of microservices. And so we need to look to SOA (service-oriented architecture) for a lot of things.

important Information: Everything runs stateless. No state. Only the database.

Problems with a decentralized minecraft server but a central plugin and our way around it:
It is a small paradox to pull something apart only to make it centrally accessible again at the end. We have thought about this problem a lot and got stuck with our current solution. We don't have a direct connection between api, translator or mc services, this will only work through a message service like rabbitmq, we do this to continue the concept of asynchrony and not to introduce a complex system between client and server communication. 

Baisc idea for the technical stack:
[TECHSTACK](./TECHSTACK.md)

## Goals:
+ better performance usage as the normal minecraft server
+ better security
+ handle more players
+ more features
+ better api for plugins, concept in the direction of Minestorm
+ imitate bigger servers, to be able to handle more players on the same server
+ better use of resources (cpu, memory, disk)
+ k8s deployment
+ other stuff



## Overviews:
Basic idea overview:

![Idea as a diagram](images/idea.png)


Overview:

![Overview](images/overview.png)

Explaning the diffrent parts of the system:

- Connector: Here will the minecraft client connect to the server.
- Translator: Translates the packet from java or bedrock to a universal format. And send it into the message service.
- Message Service: The message service is the central point of the system. It will handle the communication between the api, the translator and the mc services.
- MC Services: On the mc services runs all important stuff like the world, the player, the inventory, the crafting, the chat, the command etc. for a actual minecraft server.
- API: The api is the interface between the services and the plugins.
