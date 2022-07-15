# Police K9 Scripts originally forked from hashisx https://github.com/hashisx/hashx_k9 and rereleased from FjamZoo https://github.com/FjamZoo/qb-k9

## Support On Ko-fi

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/M4M4DRR9P)

## Credits:

- Hashisx - Original creator of hashx_k9 - https://github.com/hashisx/hashx_k9/
-  FjamZoo - Maintaining and Forking to qb-k9 - https://github.com/FjamZoo/qb-k9/
- Jimathy666 - Inspiration from jim-mechanic for Dog House Prop - https://jimathy666.tebex.io/
- martinct - German Shepherd Ped Model on LCPDFR - https://www.lcpdfr.com/downloads/gta5mods/character/19996-german-shepherd-malinois-k9-dog/

### How To Use:

Purchase a dog from the location specified in the Config, use Z to follow or attack (Must be pointing a weapon to attack).

Press K to show K9 Commands (Both of these are now keymaps so its a on user basis)

### How To Install The K-9 Ped

- Take the german-shepherd file and place it in your [standalone] folder.
- Restart server
- Voila!

### Config Use

You can place dog houses in areas of your choosing. The current locations are at Gabz Davis and MRPD (MRPD is commented out)

- Screenshots Soon -

### Searching

 You must be facing your target (vehicle or player) when selecting the Search Action, except for Search Area.
 Sometimes the Search Person will pick up the dog. Best to have the dog behind you.

### You must add this to QB Inventory Server main.lua.
```
    local function HasItem(list, item)

        for i = 1, #list do

            if item == list[i] then
                return true
            end
        end

        return false
    end

    AddEventHandler("inventory:server:SearchLocalVehicleInventory", function(plate, list, cb)
    local trunk = Trunks[plate]
    local glovebox = Gloveboxes[plate]
    local result = false

    if trunk ~= nil then
        for k, v in pairs(trunk.items) do
            local ITEM = trunk.items[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    else
        trunk = GetOwnedVehicleItems(plate)

        for k, v in pairs(TRUNK) do

            local ITEM = TRUNK[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end

    end

    if glovebox ~= nil then
        for k, v in pairs(glovebox.items) do

            local ITEM = glovebox.items[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    else
        glovebox = GetOwnedVehicleGloveboxItems(plate)

        for k, v in pairs(glovebox) do
            local ITEM = glovebox[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    end
    cb(RESULT)
end)
```
