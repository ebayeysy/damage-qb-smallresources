# damage-qb-smallresources
- เป็นสคริปปรับดาเมจของ qb-smallresources

> สร้างไฟล์ qb-smallresources\client\main.lua
> ```js
> Citizen.CreateThread(function()
>    while Config.Weapondamage == nil do
>        TriggerEvent('getWeaponDamageConfig', function(cfg)
>            config = cfg
>        end)
>        Wait(1000) 
>    end
>end)
>
>RegisterNetEvent('getWeaponDamageConfig')
>AddEventHandler('getWeaponDamageConfig', function(callback)
>    callback(config)
>end)
>
>Citizen.CreateThread(function()
>    while true do
>        local playerPed = PlayerPedId()
>        local weapon = GetSelectedPedWeapon(playerPed)
>        local weaponHash = GetHashKey(weapon)
>
>        local damage = Config.Weapondamage[weaponHash]
>        if damage ~= nil then
>            TriggerServerEvent('playerFiredWeapon', weapon, damage)
>        end
>
>        Wait(1000)
>    end
>end)
>
> ```

> qb-smallresources\config.lua
> ```js
>Config.Weapondamage = { 
>    ["WEAPON_UNARMED"] = 0.2,
>    ["WEAPON_KNIFE"] = 0.5,
>   -- ["WEAPON_SPECIALCARBINE_MK2"] = 0.1,
>    -- ["WEAPON_BULLPUPRIFLE_MK2"] = 0.1,
>    -- ["WEAPON_PUMPSHOTGUN_MK2"] = 0.1
>}
>
> ```
