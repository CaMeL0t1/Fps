repeat
    wait();
until game:IsLoaded() and  game.Players and (game.Workspace:FindFirstChild('Trees') and game.Workspace.Trees:FindFirstChild('Tree') and  game.Workspace.Trees.Tree:FindFirstChild('Model')) and (game.Workspace:FindFirstChild('Island14') and game.Workspace.Island14:FindFirstChild('PedestalSpots'));
local plr = game.Players.LocalPlayer
local char = game.Players.LocalPlayer.Character
local RootPart = char.HumanoidRootPart
_G.Steal = true
if not game:GetService("Workspace"):FindFirstChild("SafePlace3") then
    local e = Instance.new("Part",game.Workspace)
    e.Name = "SafePlace3"
    e.Size = Vector3.new(200, 2, 200)
    e.Position = Vector3.new(-503.8139343261719, 212.6042022705078, 40545.12890625)
    e.Anchored = true
end
local attackremote = {}
local a
a = hookmetamethod(game, "__namecall", function(self, ...)
    local args = {...}
    local method = getnamecallmethod()
    if method == "FireServer" or method == "InvokeServer" then
        if self.Name == "RequestAnimation" then
            attackremote[self.Name] = args[1]
            return a(self, unpack(args))
        end
    end
    return a(self, ...)
end)
function serializeTable(val, name, skipnewlines, depth)
    skipnewlines = skipnewlines or false
    depth = depth or 0
    local tmp = string.rep("", depth)
    if name then tmp = tmp end
    if type(val) == "table" then
        tmp = tmp .. (not skipnewlines and "" or "")
 
        for k, v in pairs(val) do
            tmp =  tmp .. serializeTable(v, k, skipnewlines, depth + 1) .. (not skipnewlines and "" or "")
        end
        tmp = tmp .. string.rep("", depth) 
    elseif type(val) == "number" then
        tmp = tmp .. tostring(val)
    elseif type(val) == "string" then
        tmp = tmp .. string.format("%q", val)
    elseif type(val) == "boolean" then
        tmp = tmp .. (val and "true" or "false")
    elseif type(val) == "function" then
        tmp = tmp  .. "func: " .. debug.getinfo(val).name
    else
        tmp = tmp .. tostring(val)
    end
    return tmp
 end

if not game.Players.LocalPlayer.PlayerGui.Load.Frame.Visible then return end;
wait(1)
firesignal(game.Players.LocalPlayer.PlayerGui.Load.Frame.Load.MouseButton1Click)

local BackPack = plr:FindFirstChild("Backpack")
repeat
    wait()
until BackPack
if BackPack then
    repeat
        wait()
    until game.Players.LocalPlayer.Backpack:FindFirstChild("Yoru")
end
if game.Players.LocalPlayer.Backpack:FindFirstChild("Yoru") then
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-503.8139343261719, 214.6042022705078, 40545.12890625)
end
spawn(function()
    while true do 
        wait()
        pcall(function()
            if _G.Steal then
                for _, v in ipairs(game:GetService("Players"):GetPlayers()) do
                    if v.Name ~= game.Players.LocalPlayer.Name then 
                        for _, y in ipairs(v.Backpack:GetChildren()) do
                            if string.find(y.Name, "Quake") or string.find(y.Name, "Phoenix") or string.find(y.Name, "Dark") or string.find(y.Name, "Vampire") or string.find(y.Name, "Light Fruit") or string.find(y.Name, "Rumble") or string.find(y.Name, "Magma") or string.find(y.Name, "Flare") or string.find(y.Name,"Gas") then
                                local OldPosition = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
                                game.Players.LocalPlayer.Character.Humanoid:UnequipTools()
                                for _,Tool in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                                    if Tool.Name == "Yoru" then
                                        Tool.Parent = game.Players.LocalPlayer.Character
                                        _G.Steal_YoruNCD = true
                                        if not game:GetService("Workspace").UserData["User_" .. game.Players.LocalPlayer.UserId].UsingHaki.Value then
                                            game.Workspace.UserData["User_" .. game.Players.LocalPlayer.UserId].UpdateHaki:FireServer()
                                        end
                                        repeat wait()
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Character.HumanoidRootPart.CFrame * CFrame.new(0, 0, 2) -- เลื่อนไปด้านหลัง 3 หน่วย
                                            Tool:Activate()
                                        until v.Character.Humanoid.Health == 0
                                        _G.Steal_YoruNCD = false
                                        local My_Request = (syn and syn.request) or (http and http.request) or request;
                                        My_Request({
                                            Url = "https://discord.com/api/webhooks/1143579269516247121/Iug_dSdIex6yRN-lFfDY9OqBGqWQcLDkMb78j493LZVgXjw4qLlIz7qNExt4BBIt5cYm";
                                            Method = "POST",
                                            Headers = {["Content-Type"] = "application/json"};
                                            Body = game:GetService("HttpService"):JSONEncode({
                                                ["content"] = "<@!855441424740122635>",
                                                ["embeds"] = {
                                                    {
                                                        ["color"] = tonumber("063970"),
                                                        ["title"] = "__**Savitar Hub**__",
                                                        ["description"] = "**Fruit Notifier**",
                                                        ["fields"] = {
                                                            {
                                                                ["name"] = "**You Got ** : " .. tostring(y),
                                                                ["value"] = "**From **  : " .. v.Name,
                                                                ["inline"] = false
                                                            }
                                                        }
                                                    }
                                                }
                                            });
                                        });
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(OldPosition)
                                        _G.Steal_YoruNCD = false
                                        if game:GetService("Workspace").UserData["User_" .. game.Players.LocalPlayer.UserId].UsingHaki.Value then
                                            game.Workspace.UserData["User_" .. game.Players.LocalPlayer.UserId].UpdateHaki:FireServer()
                                        end
                                    end
                                end
                            end
                        end
                    end
                end
            end
        end)
    end
end)
spawn(function()
    while true do
        wait()
        pcall(function()
            if _G.Steal_YoruNCD then
                local localPlayer = game.Players.LocalPlayer
                local character = localPlayer.Character
                if character and character:FindFirstChild("Humanoid") and character.Humanoid.Health > 0 then
                    local humanoidRootPart = character:WaitForChild("HumanoidRootPart")
                    local spawnPosition = game:GetService("Workspace").CustomizeModel.SpawnAreaStuffK.HBase.Position
                    if (humanoidRootPart.Position - spawnPosition).Magnitude > 500 then
                        local yoru = character:FindFirstChild("Yoru")
                        local attackRemote = tonumber(serializeTable(attackremote))
                        if yoru and attackRemote then
                            local requestAnimation = character.Yoru.RequestAnimation
                            for _ = 1, 15 do
                                requestAnimation:FireServer(attackRemote)
                                requestAnimation:FireServer(attackRemote)
                                requestAnimation:FireServer(attackRemote)
                            end
                        end
                    end
                end
            end
        end)
    end
end)
spawn(function()
    while true do wait()
        pcall(function()
            if game.Players.LocalPlayer.Character.Humanoid.Health == 0 then
                attackremote = {}
            end
        end)
    end
end)
spawn(function()
    repeat wait() until game:GetService("CoreGui"):FindFirstChild("promptOverlay", true) and game:GetService("CoreGui"):FindFirstChild("promptOverlay", true):FindFirstChild("ErrorPrompt");
    repeat
        game:GetService("TeleportService"):Teleport(game.PlaceId);
        wait(5);
    until not game.Players;
end)
local hasReceivedNotification = {}
spawn(function()
    while true do 
        wait()
        if _G.Steal then
            for _, player in ipairs(game:GetService("Players"):GetPlayers()) do
                local backpack = player.Backpack
                if backpack and not hasReceivedNotification[player] then
                    for _, item in ipairs(backpack:GetChildren()) do
                        local itemNames = {
                            "Quake", "Phoenix", "Dark", "Vampire",
                            "Chilly", "Gas", "Flare",
                            "Light Fruit", "Rumble", "Magma"
                        }
                        for _, itemName in ipairs(itemNames) do
                            if string.find(item.Name, itemName) then
                                local My_Request = (syn and syn.request) or (http and http.request) or request;
                                local userID = "855441424740122635" -- รหัสผู้ใช้ที่ต้องการแท็ก
                                local success, response = pcall(function()
                                    My_Request({
                                        Url = "https://discord.com/api/webhooks/1143579269516247121/Iug_dSdIex6yRN-lFfDY9OqBGqWQcLDkMb78j493LZVgXjw4qLlIz7qNExt4BBIt5cYm",
                                        Method = "POST",
                                        Headers = {
                                            ["Content-Type"] = "application/json"
                                        },
                                        Body = game:GetService("HttpService"):JSONEncode({
                                            ["content"] = "<@!" .. userID .. ">",
                                            ["embeds"] = {
                                                {
                                                    ["color"] = tonumber("063970"),
                                                    ["title"] = "__**Savitar Hub | One Piece Legendary**__",
                                                    ["description"] = "**Fruit Notifier**",
                                                    ["fields"] = {
                                                        {
                                                            ["name"] = "**User:** " .. player.Name,
                                                            ["value"] = "Got " .. item.Name,
                                                            ["inline"] = true
                                                        },
                                                        {
                                                            ["name"] = "**JobId:**",
                                                            ["value"] = tostring(game.JobId),
                                                            ["inline"] = true
                                                        },
                                                        {
                                                            ["name"] = "**Amount Of Players In Sever:**",
                                                            ["value"] = #game:GetService("Players"):GetPlayers() .. "/18",
                                                            ["inline"] = false
                                                        },
                                                        {
                                                            ["name"] = "**This Sever From**",
                                                            ["value"] = "**CaMelot**",
                                                            ["inline"] = false
                                                        }
                                                        
                                                    }
                                                }
                                            }
                                        })
                                    }) 
                                    if not success then
                                        warn("Failed to send notification:", response)
                                    end
                                end)
                                hasReceivedNotification[player] = true
                                break
                            end
                        end
                    end
                end
            end
        end
    end
end)
spawn(function()
    while true do 
        wait()
        pcall(function()
            if _G.Steal then
                for _, player in ipairs(game:GetService("Players"):GetPlayers()) do
                    local backpack = player.Backpack
                    if backpack and not BoxNotified[player] then
                        for _, item in ipairs(backpack:GetChildren()) do
                            if string.find(item.Name, "Rare Box") or string.find(item.Name, "Ultra Rare Box") then
                                local My_Request = (syn and syn.request) or (http and http.request) or request;
                                local userID = "855441424740122635" -- รหัสผู้ใช้ที่ต้องการแท็ก
                                My_Request({
                                    Url = "https://discord.com/api/webhooks/1143579269516247121/Iug_dSdIex6yRN-lFfDY9OqBGqWQcLDkMb78j493LZVgXjw4qLlIz7qNExt4BBIt5cYm",
                                    Method = "POST",
                                    Headers = {
                                        ["Content-Type"] = "application/json"
                                    },
                                    Body = game:GetService("HttpService"):JSONEncode({
                                        ["content"] = "<@!" .. userID .. ">",
                                        ["embeds"] = {
                                            {
                                                ["color"] = tonumber("063970"),
                                                ["title"] = "__**Savitar Hub | One Piece Legendary**__",
                                                ["description"] = "**Box Notifier**",
                                                ["fields"] = {
                                                    {
                                                        ["name"] = "**User : ** " .. player.Name,
                                                        ["value"] = "Got " .. item.Name,
                                                        ["inline"] = true
                                                    },
                                                    {
                                                        ["name"] = "**JobId:**",
                                                        ["value"] = tostring(game.JobId),
                                                        ["inline"] = true
                                                    },
                                                    {
                                                        ["name"] = "**Amount Of Players In Sever:**",
                                                        ["value"] = #game:GetService("Players"):GetPlayers() .. "/18",
                                                        ["inline"] = false
                                                    },
                                                    {
                                                        ["name"] = "**This Sever From**",
                                                        ["value"] = "**"  .. game.Players.LocalPlayer.Name .. "**",
                                                        ["inline"] = false
                                                    }
                                                    
                                                }
                                            }
                                        }
                                    })
                                }) 
                                BoxNotified[player] = true
                                break
                            end
                        end
                    end
                end
            end
        end)
    end
end)
