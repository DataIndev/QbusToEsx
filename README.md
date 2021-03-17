# QbusToEsx Converting Qbus Scripts to ESX..
--------------------------------------------------------------------------------------------------
Qbus Foundation And ESX Foundation.

 ```lua
QBCore = nil 

Citizen.CreateThread(function()
	while QBCore == nil do
		TriggerEvent('QBCore:GetObject', function(obj) QBCore = obj end)
		Citizen.Wait(30) -- Saniye Bekletme
	end
end)
```
# QBUSCORE ON TOP

# I meet ESX
```lua
ESX = nil

Citizen.CreateThread(function()
  while ESX == nil do
    TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)
    Citizen.Wait(30)-- Saniye Bekletme
  end
end)
```
--------------------------------------------------------------------------------------------------
The Player Entry Part I Need While Entering the Game, So Server File

```lua
RegisterNetEvent('QBCore:Client:OnPlayerLoaded')
AddEventHandler('QBCore:Client:OnPlayerLoaded', 
```
# QBUSCORE ON TOP

# I meet ESX
```lua
RegisterNetEvent('esx:playerLoaded')
AddEventHandler('esx:playerLoaded',
```
--------------------------------------------------------------------------------------------------
The Server File is the Job Part, the Job Part.
```lua
RegisterNetEvent('QBCore:Client:OnJobUptade')
AddEventHandler('QBCore:Client:OnJobUptade', 
```
# QBUSCORE ON TOP

# I meet ESX
```lua
RegisterNetEvent('esx:setJob')
AddEventHandler('esx:setJob',
```
--------------------------------------------------------------------------------------------------
Gentlemen, This section was not available.
Meaning:
This event is triggered when the player connects to the server
```lua
RegisterNetEvent('QBCore:Client:OnPlayerLoaded')
AddEventHandler('QBCore:Client:OnPlayerLoaded',
```
# QBUSCORE ON TOP

# I meet ESX
```lua
RegisterNetEvent('esx:playerLoaded')
AddEventHandler('esx:playerLoaded',
```
--------------------------------------------------------------------------------------------------
Adding 3D Text, Cilent File. Sample : https://media.discordapp.net/attachments/623207764314816562/812096508786507806/resim_1.png
```lua
QBCore.Functions.DrawText3D(1, 1, 1, 'Örnek')
```
# QBUSCORE ON TOP

# I meet ESX
```lua
DrawText3D(1, 1, 1, 'Örnek') -- (aşağısına function açmanız gerekmektedir.)
```
--------------------------------------------------------------------------------------------------
Menu Open Close Menus in ESX & QBCore Examples : https://prnt.sc/u4f7s5
```lua
QBCore.UI.Menu.Open
QBCore.UI.Menu.CloseAll() -- (menu default scripti kurmanız gerekmektedir.)
```
# QBUSCORE ON TOP

# I meet ESX
```lua
ESX.UI.Menu.Open
ESX.UI.Menu.CloseAll()
```
--------------------------------------------------------------------------------------------------
Notification Script Example : https://dosya.turkmmo.com/2020/09/36521_efa54848705a4069cbedfc2770e50cf1.png
```lua
QBCore.Functions.Notify("Araç kitlendi.", "error")
```
# QBUSCORE ON TOP

# I meet ESX
```lua
TriggerEvent('Notification',"Örnek.")
```
--------------------------------------------------------------------------------------------------
Enventer Item Part.
```lua
xPlayer.Functions.GetItemByName 
```
# QBUSCORE ON TOP

# I meet ESX
```lua
xPlayer.getInventoryItem
```
--------------------------------------------------------------------------------------------------
Give Money Receive Part
```lua
ply.Functions.AddMoney('bank', amount, "Bank depost") -- banka
ply.Functions.RemoveMoney('cash', amount, "Bank depost") -- üstündeki para
```
# QBUSCORE ON TOP

# I meet ESX
```lua
xPlayer.removeAccountMoney('bank', amount) --para kaldırma
xPlayer.addMoney(amount) -- para ekleme
```
--------------------------------------------------------------------------------------------------
Money Portion Data.
```lua
ply.PlayerData.money["bank"]
```
# QBUSCORE ON TOP

# I meet ESX
```lua
xPlayer.getAccount('bank').money
```
--------------------------------------------------------------------------------------------------
Inventory Item Deletion Section.
```lua
xPlayer.Functions.RemoveItem 
```
# QBUSCORE ON TOP

# I meet ESX
```lua
xPlayer.removeInventoryItem 
```
--------------------------------------------------------------------------------------------------
Adding Inventory Item Part.
```lua
xPlayer.Functions.AddItem
```
# QBUSCORE ON TOP

# I meet ESX
```lua
xPlayer.addInventoryItem
```
--------------------------------------------------------------------------------------------------
The Character Is Something Like The Id of The Gamer
```lua
QBCore.Functions.GetPlayer(src)
```
# QBUSCORE ON TOP

# I meet ESX
```lua
ESX.GetPlayerFromId(src)
```
--------------------------------------------------------------------------------------------------
Car Spawn Part Location Etc. Things.
```lua
QBCore.Functions.SpawnVehicle()
QBCore.Functions.GetVehicleProperties()
QBCore.Functions.GetClosestVehicle()
```
# QBUSCORE ON TOP

# I meet ESX
```lua
ESX.Game.SpawnVehicle()
ESX.Game.GetVehicleProperties()
ESX.Game.GetClosestVehicle()
```
- (Almost everything you have in ESX.Game is the same as QBCore.Functions.)
- --------------------------------------------------------------------------------------------------
Player Your Own Character.
```lua
QBCore.Functions.GetPlayerData()
```
# QBUSCORE ON TOP

# I meet ESX
```lua
ESX.GetPlayerData()
```
--------------------------------------------------------------------------------------------------
Creating Item.
```lua
QBCore.Functions.CreateUseableItem()
```
# QBUSCORE ON TOP

# I meet ESX
```lua
ESX.RegisterUsableItem()
```
--------------------------------------------------------------------------------------------------
Related to Files.
```lua
QBCore.Functions.CreateCallback()
```
# QBUSCORE ON TOP

# I meet ESX
```lua
ESX.RegisterServerCallback()
```
--------------------------------------------------------------------------------------------------
Related to Files.
```lua
QBCore.Functions.TriggerCallback()
```
# QBUSCORE ON TOP

# I meet ESX
```lua
ESX.TriggerServerCallback()
```
--------------------------------------------------------------------------------------------------
Using identifier in cid esx in qb I left a small block of code for you to solve the case.
```lua
QBCore.Functions.CreateCallback('system:fetchStatus', function(source, cb)
    local Player = QBCore.Functions.GetPlayer(source)

     if Player then
           exports['ghmattimysql']:execute('SELECT skills FROM players WHERE citizenid = @citizenid', {
               ['@citizenid'] = Player.PlayerData.citizenid
          }, function(status)
              if status ~= nil then
                   cb(json.decode(status))
              else
                   cb(nil)
              end
          end)
     else
          cb()
     end
end)
```
# QBUSCORE ON TOP

# I meet ESX
```lua
ESX.RegisterServerCallback("system:fetchStatus", function(source, cb)
    local src = source
    local user = ESX.GetPlayerFromId(src)


    local fetch = [[
         SELECT
              skills
         FROM
              users
         WHERE
              identifier = @identifier
    ]]

    MySQL.Async.fetchScalar(fetch, {
         ["@identifier"] = user.identifier

    }, function(status)

         if status ~= nil then
              cb(json.decode(status))
         else
              cb(nil)
         end

    end)
end)
```
--------------------------------------------------------------------------------------------------
Sql linking part
```lua
QBCore.Functions.ExecuteSql()
```
# QBUSCORE ON TOP

# I meet ESX
```lua
ESX.ExecuteSql() --(ghmattimysql)
MySQL.Async.execute()
```
--------------------------------------------------------------------------------------------------
RegisterCommand - the command part of the chat.
```lua
QBCore.Commands.Add()
```
# QBUSCORE ON TOP

# I meet ESX
```lua
RegisterCommand 
```
-- (RegisterCommand qbcore'da da çalışır.)
--------------------------------------------------------------------------------------------------
Linking to a Data Test is a Character Part
```lua
local Player = QBCore.Functions.GetPlayer(source)
['@citizenid'] = Player.PlayerData.citizenid
```
# QBUSCORE ON TOP

# I meet ESX
```lua
local user : ESX.Get.PlayerFromId(src)
["@identifier"] = user.identifier
```
--------------------------------------------------------------------------------------------------
