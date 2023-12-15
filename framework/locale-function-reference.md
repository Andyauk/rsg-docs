---
description: Learn about and how to use common core locale functions!
---

# Locale Functions

Use this template to the bottom of the file

```lua
if GetConvar('rsg_locale', 'en') == 'NAME' then
    Lang = Locale:new({
        phrases = Translations,
        warnOnMissing = true,
        fallbackLang = Lang,
    })
end
```

NAME = name of the Lang file, ie fr (French),de (Germany) ect

--

Use this template to the bottom of the file if just en (English)

```lua
Lang = Locale:new({
    phrases = Translations,
    warnOnMissing = true
})
```