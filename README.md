# 6ft

## Quest System

### Brief

Design a Quest System interface in C++. Design data structures, classes, function signatures, and DB tables supporting a player questing system with the following characteristics.

Quest States:

``` c++
UNAVAILABLE // unavailable for whatever reason
AVAILABLE   // available but not yet obtained
OBTAINED    // obtained with no objectives completed
IN-PROGRESS // obtained with some objectives completed
COMPLETED   // obtained with all objectives completed
```

Other Requirements:

- Quests can have prerequisites that must be completed to transition to the AVAILABLE state
- Quests allow "N of M objectives, N<=M" for transition to the COMPLETED state
- Quests in the COMPLETED state can grant achievements

Be sure to explain any assumptions your design makes using code comments.

### Assumptions

- 1.0 The quest system is for a MMORPG.
  - 1.1 Quests can be added to the game.
  - 1.2 Quests can be gobally disabled (such as holiday or event-related quests).
  - 1.3 Quests can only be updated while the game servers are in maintance mode.
- 2.0 All objects in game can have a UUID.
  - 2.1 Given a UUID, an object can be created.
  - 2.2 Given an object, a UUID can be derived.
  - 2.3 UUIDs and objects can be used interchangably.
- 3.0 There exists a robust event system.
  - 3.1 Events provide an event type (`ENEMY_KILLED`, `ITEM_COLLECTED`, `VOLUME_ENTERED`, _et cetera_).
  - 3.2 Events provide a value (`Enraged_Panther`, `Refined_Ore`, `Enemy_Base_Entrance`, _et cetera_).
  - 3.3 The event system provides an interface for recieving events, `IGameEventListener`.
  - 3.4 The event system provides an interface for sending events, `IGameEventDispatcher`.
- 4.0 Quest objectives are based on discrete, numerical values, such as:
  > - __Bless Pirates__ 13/20
  > - __Taste Pies__ 5/8
  > - __Complete Programming Test__ 0/1
- 5.0 There exists a Loot object that can support any possible quest rewards.

### Design Approach

![Class Diagram](out/quest-system-class-diagram/quest-system-class-diagram.svg)

![State Diagram](out/quest-system-event-diagram/quest-system-event-diagram.svg)

When a quest is available, it will appear in-game for the Player.

### Database

#### Quest

|id|name|description|isAvailable|
|--|----|-----------|-----------|
|1|Gunrunning 101|We need you to deliver a shipment of laser rifles to Al Cadus. While you're at it, go ahead and clear the route of any USM Spydrones you find.|true|
|2|"F" For Effort|Well, that drop went to shit. Search the wreckage and see if you can find anything that might help us figure out how the hell USM found out about the deal.|true|
|3|Santa's Big Helper|Al Cadus placed a rush order for the holidays, and they need it _yesterday_. Get these crates of "Festive Eggnog" (it's guns) to them ASAP.|false|
