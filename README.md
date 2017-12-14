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

### Database

#### Quest

|id|name|description|isAvailable|
|--|----|-----------|-----------|
|1|Gunrunning 101|We need you to deliver a shipment of laser rifles to Al Cadus. While you're at it, go ahead and clear the route of any USM Spydrones you find.|true|
|2|"F" For Effort|Well, that drop went to shit. Search the wreckage and see if you can find anything that might help us figure out how the hell USM found out about the deal.|true|
|3|Santa's Big Helper|Al Cadus placed a rush order for the holidays, and they need it _yesterday_. Get these crates of "Festive Eggnog" (it's guns) to them ASAP.|false|
