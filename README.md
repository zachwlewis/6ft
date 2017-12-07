# 6ft

## Quest System

### Goal

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
