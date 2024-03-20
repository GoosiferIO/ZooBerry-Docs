# Operating on Entities

!!! warning "Difficulty: Advanced"

First, let's get some lingo out of the way. Entities are what the game calls anything that can be bought and placed on the map. This includes animals, guests, staff, and scenery. In the context of the low level game machinations, there are two concepts to understand here: entities and entity types. An entity is an instance of an entity type. For example, an African Elephant is an entity type, and an "African Elephant 1" that you place in your zoo is an entity. 

Each entity has a unique ID that the game uses to reference it. For example, the African Elephant has the ID `elephant_african`. You can find a list of these IDs in the [official string tables](./string-tables/official/).