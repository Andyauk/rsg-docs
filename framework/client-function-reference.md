---
description: Learn about and how to use common core client functions!
---

# Client Function Reference

### RSGCore.Functions.GetPlayerData

* Perhaps the most used function in the framework. This function returns the players data of the current source which, since its used client side, is automatically the client or player. It can be used with modifiers on the end starting with a "." (period)

```lua
function RSGCore.Functions.GetPlayerData(cb)
    if not cb then return RSGCore.PlayerData end
    cb(RSGCore.PlayerData)
end

-- Example

local Player = RSGCore.Functions.GetPlayerData()
print(RSGCore.Debug(Player))

OR

local Player = RSGCore.Functions.GetPlayerData()
local jobName = Player.job.name
print(jobName)
```

### RSGCore.Functions.GetCoords

* This function operates very similarly to how the native GetEntityCoords does, but it returns the heading as well

```lua
function RSGCore.Functions.GetCoords(entity)
    return vector4(GetEntityCoords(entity), GetEntityHeading(entity))
end

-- Example

local coords = RSGCore.Functions.GetCoords(PlayerPedId())
print(coords)
```

### RSGCore.Functions.HasItem

* Returns whether a player has a certain item

```lua
function RSGCore.Functions.HasItem(item)
    local p = promise.new()
    RSGCore.Functions.TriggerCallback('RSGCore:HasItem', function(result)
        p:resolve(result)
    end, item)
    return Citizen.Await(p)
end

-- Example

local hasItem = RSGCore.Functions.HasItem('my_cool_item')
print(hasItem)
```

### RSGCore.Functions.TriggerCallback

* Function used to call from the client to the server and receive a value back

```lua
function RSGCore.Functions.TriggerCallback(name, cb, ...)
    RSGCore.ServerCallbacks[name] = cb
    TriggerServerEvent('RSGCore:Server:TriggerCallback', name, ...)
end

-- Example

RSGCore.Functions.TriggerCallback('callbackName', function(result)
    print('I got this from the CreateCallBack -->  '..result)
end, 'my_parameter_name')
```

### RSGCore.Functions.GetVehicles

* Returns vehicle game pool (for backwards compatibility) - Not worth using

```lua
function RSGCore.Functions.GetVehicles()
    return GetGamePool('CVehicle')
end

-- Example

local vehicles = RSGCore.Functions.GetVehicles()
print(RSGCore.Debug(vehicles))

OR -- preferred method

local vehicles = GetGamePool('CVehicle')
print(RSGCore.Debug(vehicles))
```

### RSGCore.Functions.GetCoreObject

* Returns the core object for accessing

```lua
exports('GetCoreObject', function()
    return QBCore
end)

-- Example

local RSGCore = exports['rsg-core']:GetCoreObject()

OR -- call the core in a single file that loads before the others

RSGCore = exports['rsg-core']:GetCoreObject()
```

### RSGCore.Functions.GetPlayers

* Returns active players in OneSync scope (for backwards compatibility) - Not worth using

```lua
function RSGCore.Functions.GetPlayers()
    return GetActivePlayers()
end

-- Example

local players = RSGCore.Functions.GetPlayers()
print(RSGCore.Debug(players))

OR -- preferred method

local players = GetActivePlayers()
print(RSGCore.Debug(players))
```

### RSGCore.Functions.GetPeds

* Returns a model hash filtered ped game pool

```lua
function RSGCore.Functions.GetPeds(ignoreList -- [[table]])
    local pedPool = GetGamePool('CPed')
    local ignoreList = ignoreList or {}
    local peds = {}
    for i = 1, #pedPool, 1 do
        local found = false
        for j=1, #ignoreList, 1 do
            if ignoreList[j] == pedPool[i] then
                found = true
            end
        end
        if not found then
            peds[#peds+1] = pedPool[i]
        end
    end
    return peds
end

-- Example

local peds = RSGCore.Functions.GetPeds({`mp_m_freemode_01`})
print(RSGCore.Debug(peds))
```

### RSGCore.Functions.GetClosestPed

* Returns the closest ped to the player after filtering

```lua
function RSGCore.Functions.GetClosestPed(coords, ignoreList)
    local ped = PlayerPedId()
    if coords then
        coords = type(coords) == 'table' and vec3(coords.x, coords.y, coords.z) or coords
    else
        coords = GetEntityCoords(ped)
    end
    local ignoreList = ignoreList or {}
    local peds = RSGCore.Functions.GetPeds(ignoreList)
    local closestDistance = -1
    local closestPed = -1
    for i = 1, #peds, 1 do
        local pedCoords = GetEntityCoords(peds[i])
        local distance = #(pedCoords - coords)

        if closestDistance == -1 or closestDistance > distance then
            closestPed = peds[i]
            closestDistance = distance
        end
    end
    return closestPed, closestDistance
end

-- Example

local coords = GetEntityCoords(PlayerPedId())
local closestPed, distance = RSGCore.Functions.GetClosestPed(coords)
print(closestPed, distance)
```

### RSGCore.Functions.GetClosestVehicle

* Returns the closest vehicle to the player

```lua
function RSGCore.Functions.GetClosestVehicle(coords)
    local ped = PlayerPedId()
    local vehicles = GetGamePool('CVehicle')
    local closestDistance = -1
    local closestVehicle = -1
    if coords then
        coords = type(coords) == 'table' and vec3(coords.x, coords.y, coords.z) or coords
    else
        coords = GetEntityCoords(ped)
    end
    for i = 1, #vehicles, 1 do
        local vehicleCoords = GetEntityCoords(vehicles[i])
        local distance = #(vehicleCoords - coords)

        if closestDistance == -1 or closestDistance > distance then
            closestVehicle = vehicles[i]
            closestDistance = distance
        end
    end
    return closestVehicle, closestDistance
end

-- Example

local coords = GetEntityCoords(PlayerPedId())
local closestVehicle, distance = RSGCore.Functions.GetClosestVehicle(coords)
print(closestVehicle, distance)
```

### RSGCore.Functions.GetClosestObject

* Returns the closest object to the player

```lua
function RSGCore.Functions.GetClosestObject(coords)
    local ped = PlayerPedId()
    local objects = GetGamePool('CObject')
    local closestDistance = -1
    local closestObject = -1
    if coords then
        coords = type(coords) == 'table' and vec3(coords.x, coords.y, coords.z) or coords
    else
        coords = GetEntityCoords(ped)
    end
    for i = 1, #objects, 1 do
        local objectCoords = GetEntityCoords(objects[i])
        local distance = #(objectCoords - coords)
        if closestDistance == -1 or closestDistance > distance then
            closestObject = objects[i]
            closestDistance = distance
        end
    end
    return closestObject, closestDistance
end

-- Example

local coords = GetEntityCoords(PlayerPedId())
local closestObject, distance = RSGCore.Functions.GetClosestObject(coords)
print(closestObject, distance)
```

### RSGCore.Functions.GetClosestPlayer

* Returns the closest player to the client

```lua
function RSGCore.Functions.GetClosestPlayer(coords)
    local ped = PlayerPedId()
    if coords then
        coords = type(coords) == 'table' and vec3(coords.x, coords.y, coords.z) or coords
    else
        coords = GetEntityCoords(ped)
    end
    local closestPlayers = RSGCore.Functions.GetPlayersFromCoords(coords)
    local closestDistance = -1
    local closestPlayer = -1
    for i = 1, #closestPlayers, 1 do
        if closestPlayers[i] ~= PlayerId() and closestPlayers[i] ~= -1 then
            local pos = GetEntityCoords(GetPlayerPed(closestPlayers[i]))
            local distance = #(pos - coords)

            if closestDistance == -1 or closestDistance > distance then
                closestPlayer = closestPlayers[i]
                closestDistance = distance
            end
        end
    end
    return closestPlayer, closestDistance
end

-- Example

local coords = GetEntityCoords(PlayerPedId())
local closestPlayer, distance = RSGCore.Functions.GetClosestPlayer(coords)
print(closestPlayer, distance)
```

### QBCore.Functions.GetPlayersFromCoords

* Returns all players within a radius of specific coordinates

```lua
function RSGCore.Functions.GetPlayersFromCoords(coords, distance)
    local players = RSGCore.Functions.GetPlayers()
    local ped = PlayerPedId()
    if coords then
        coords = type(coords) == 'table' and vec3(coords.x, coords.y, coords.z) or coords
    else
        coords = GetEntityCoords(ped)
    end
    local distance = distance or 5
    local closePlayers = {}
    for _, player in pairs(players) do
        local target = GetPlayerPed(player)
        local targetCoords = GetEntityCoords(target)
        local targetdistance = #(targetCoords - coords)
        if targetdistance <= distance then
            closePlayers[#closePlayers + 1] = player
        end
    end
    return closePlayers
end

-- Example

local coords = GetEntityCoords(PlayerPedId())
local radius = 5.0
local closestPlayers = RSGCore.Functions.GetPlayersFromCoords(coords, radius)
print(RSGCore.Debug(closestPlayers))
```
