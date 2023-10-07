---
description: Learn about and how to use common core client events!
---

# Client Event Reference

### RSGCore:Client:OnPlayerLoaded

* Handles the player loading in after character selection

{% hint style="success" %}
This event can be used as an event handler to trigger code because it signifies the player has successfully loaded into the server!
{% endhint %}

```lua
RegisterNetEvent('RSGCore:Client:OnPlayerLoaded', function()
    print('Im a client and i just loaded into your server!')
end)
```

### RSGCore:Client:OnPlayerUnload

* Handles the player login out to character selection

{% hint style="success" %}
This event can be used as an event handler to trigger code because it signifies the player has successfully unloaded or logged out of the server!
{% endhint %}

```lua
RegisterNetEvent('RSGCore:Client:OnPlayerUnload', function()
    print('Im a client and i just logged out of your server!')
end)
```
