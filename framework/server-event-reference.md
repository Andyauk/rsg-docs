---
description: Learn about and how to use common core server events!
---

# Server Events

## RSGCore:Server:CloseServer
Event to check if the server is closed

```lua
RegisterNetEvent('RSGCore:Server:CloseServer', function(reason)
    local src = source
    if RSGCore.Functions.HasPermission(src, 'admin') then
        reason = reason or 'No reason specified'
        RSGCore.Config.Server.Closed = true
        RSGCore.Config.Server.ClosedReason = reason
        for k in pairs(RSGCore.Players) do
            if not RSGCore.Functions.HasPermission(k, RSGCore.Config.Server.WhitelistPermission) then
                RSGCore.Functions.Kick(k, reason, nil, nil)
            end
        end
    else
        RSGCore.Functions.Kick(src, 'You don\'t have permissions for this..', nil, nil)
    end
end)
```

## RSGCore:Server:OpenServer
Event to check if the server is open

```lua
RegisterNetEvent('RSGCore:Server:OpenServer', function()
    local src = source
    if RSGCore.Functions.HasPermission(src, 'admin') then
        RSGCore.Config.Server.Closed = false
    else
        RSGCore.Functions.Kick(src, 'You don\'t have permissions for this..', nil, nil)
    end
end)
```

## RSGCore:UpdatePlayer
Event for updating and saving player data

```lua
RegisterNetEvent('RSGCore:UpdatePlayer', function()
    local src = source
    local Player = RSGCore.Functions.GetPlayer(src)
    if not Player then return end
    local newHunger = Player.PlayerData.metadata['hunger'] - RSGCore.Config.Player.HungerRate
    local newThirst = Player.PlayerData.metadata['thirst'] - RSGCore.Config.Player.ThirstRate
    if newHunger <= 0 then newHunger = 0 end
    if newThirst <= 0 then newThirst = 0 end
    Player.Functions.SetMetaData('thirst', newThirst)
    Player.Functions.SetMetaData('hunger', newHunger)
    TriggerClientEvent('hud:client:UpdateNeeds', src, newHunger, newThirst)
    Player.Functions.Save()
end)
```

## RSGCore:Server:SetMetaData
Event to set a players metadata

```lua
RegisterNetEvent('RSGCore:Server:SetMetaData', function(meta, data)
    local src = source
    local Player = RSGCore.Functions.GetPlayer(src)
    if meta == 'hunger' or meta == 'thirst' then
        if data > 100 then
            data = 100
        end
    end
    if Player then
        Player.Functions.SetMetaData(meta, data)
    end
    TriggerClientEvent('hud:client:UpdateNeeds', src, Player.PlayerData.metadata['hunger'], Player.PlayerData.metadata['thirst'])
end)
```

## RSGCore:ToggleDuty
Event to toggle a player's duty status

```lua
RegisterNetEvent('RSGCore:ToggleDuty', function()
    local src = source
    local Player = RSGCore.Functions.GetPlayer(src)
    if not Player then return end
    if Player.PlayerData.job.onduty then
        Player.Functions.SetJobDuty(false)
        TriggerClientEvent('RSGCore:Notify', src, Lang:t('info.off_duty'))
    else
        Player.Functions.SetJobDuty(true)
        TriggerClientEvent('RSGCore:Notify', src, Lang:t('info.on_duty'))
    end
    TriggerClientEvent('RSGCore:Client:SetDuty', src, Player.PlayerData.job.onduty)
end)
```

## RSGCore:CallCommand
Event to trigger a command outside the chat

```lua
RegisterNetEvent('RSGCore:CallCommand', function(command, args)
    local src = source
    if not RSGCore.Commands.List[command] then return end
    local Player = RSGCore.Functions.GetPlayer(src)
    if not Player then return end
    local hasPerm = RSGCore.Functions.HasPermission(src, "command."..RSGCore.Commands.List[command].name)
    if hasPerm then
        if RSGCore.Commands.List[command].argsrequired and #RSGCore.Commands.List[command].arguments ~= 0 and not args[#RSGCore.Commands.List[command].arguments] then
            TriggerClientEvent('RSGCore:Notify', src, Lang:t('error.missing_args2'), 'error')
        else
            RSGCore.Commands.List[command].callback(src, args)
        end
    else
        TriggerClientEvent('RSGCore:Notify', src, Lang:t('error.no_access'), 'error')
    end
end)
```