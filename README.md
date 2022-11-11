## mh-carlift
This add multi fully fonctional car lifts in your world
you can add more if you want.

***
This script is setup for my mh-scrapyardMLO
***

# Yes i know this 😁
1. Yes, there will always be platforms on the ground even if you use the car lift,
 - I did this because if I don't, the car lift won't work properly..
2. Yes on your screen if you use the lift wil work good.
 - Yes on your screen the elevator will work well and go smoothly if you use it, 
 - by other players, it can hop a little bit on there screen.
 - don't set the speed for the carlift too high.
 
 
## 📸 Screenshot 👊😁👍
![foto1](https://www.madirc.nl/fivem/scrapyardMLO/Schermafbeelding%202022-11-10%20152947.png)
![foto1](https://www.madirc.nl/fivem/scrapyardMLO/Schermafbeelding%202022-11-10%20152904.png)


# To setup other car lifts in your world
```lua
[1] = {               	                     -- this and the id, must be the same number. (a unique number)
    id        = 1,    	                     -- this needs the id from above. 
    min       = 47.37, 	                     -- lower position of the lift
    max       = 49.45, 	                     -- higher position of the lift (z from the main coords)
    beforemax = 45.53, 	                     -- detector for speed_up_slow befor the final point
    beforemin = 48.00, 	                     -- detector for speed_down_slow befor the final point
    entity    = nil,   	                     -- dont change this
    needPoles = false,                       -- if dont have poles set this true
    openMenu  = true,                        -- if you want to have a menu on the lift, false if you have other plans with it.
    workarea  = {length = 7.0, wide = 7.0 }, -- length and wide of the box zone
    job       = {"mechanic", "scrapyard"},   -- job access
    coords    = {["x"] = 2345.31, ["y"] = 3141.512, ["z"] = 47.37874, ["h"] = -189.5}, -- start base coords of this lift platform.
}, 
```

# Use the exports to get the Closest Lift ID
```lua
local id, distance, entity, coords = exports['mh-carlift']:GetClosestLiftObject()`
```

## Example to get the Closest Lift
```lua
Citizen.CreateThread(function()
    while true do
        Citizen.Wait(0)
	local id, dist, entity, coords = exports['mh-carlift']:GetClosestLiftObject()
	local elevatorCoords = GetEntityCoords(entity, false) -- to get the closest car lift near you
	Wait(100)
    end
end)
```

# Example how to use this in other scripts, to interact with the lift.
- if you have a other script and you want to move the lift up, you can use this.
```lua
local data = {}
data = {handle = "up", id = id} end   -- go up
data = {handle = "down", id = id} end -- go down
data = {handle = "stop", id = id} end -- stop

TriggerServerEvent('mh-carlift:server:use', data) -- take the data you need
```