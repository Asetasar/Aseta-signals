# Aseta-signals

Simple, lightweight and powerful module for handling signals.


### Why?

* This module was specifically made for my [Asetasar framework](https://github.com/Asetasar/Asetasar-Framework) as one of necessary internal components


### Differences from other custom signal modules

* Centralized: All callbackfunctions which are used in priority queue per signal are stored inside global lookup table for ease of debugging, cleaning up memory and other minor benefits, with no additional performance impact.
* Simple: There is no unnecessary bloat which most other signal modules suffer from, it is just simply custom signal handler, nothing more, nothing less.
* Custom garbage-collection: I had to implement custom garbage collector for arrays which store priority of signals to avoid any table shifting per iteration upon removal.
* No security nonsense: All signals can be fired by any scripts.

### Plans for future

* Find faster method of storing priority to fully avoid usage of arrays and therefore integration of GC and additional complexity
* Find approach for running signals parralerly (this could damage priority) without usage of coroutines, tasks, spawns as those simply move function on another linear execution.

  ## How to use

*Creation of class*

```lua
local signal = asetaSignals.New() : dictionary

--// Returns OOP class dictionary
```

*Additional usage*

```lua
local connection = signal:Connect(callbackFunction) : dictionary
                   signal:Once(callbackFunction) : dictionary
                   signal:Wait()

--// Where specified returns typical connection dictionary

connection:Disconnect()
connection:ChangeConnectionType(
    "Once"
    "Connect"
)
connection:Wait() --// Yields until another signal fire.
```

$$



$$
