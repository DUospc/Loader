-- ////////////  BLUE ELECTRO HUB - FINAL + FULL ERROR DENIAL  ////////////

-- Services
local TweenService = game:GetService("TweenService")
local Players = game:GetService("Players")
local Lighting = game:GetService("Lighting")
local RunService = game:GetService("RunService")

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- ////////////  LOADING GUI  ////////////

local loadingGui = Instance.new("ScreenGui")
loadingGui.Name = "BlueElectroLoading"
loadingGui.ResetOnSpawn = false
loadingGui.Parent = playerGui

local bg = Instance.new("Frame")
bg.Size = UDim2.new(1, 0, 1, 0)
bg.BackgroundColor3 = Color3.fromRGB(8, 8, 20)
bg.BorderSizePixel = 0
bg.Parent = loadingGui

local bgCorner = Instance.new("UICorner")
bgCorner.CornerRadius = UDim.new(0, 0)
bgCorner.Parent = bg

local bgStroke = Instance.new("UIStroke")
bgStroke.Color = Color3.fromRGB(0, 140, 255)
bgStroke.Thickness = 3
bgStroke.Transparency = 0.6
bgStroke.Parent = bg

local content = Instance.new("Frame")
content.Size = UDim2.new(0, 420, 0, 220)
content.Position = UDim2.new(0.5, -210, 0.5, -110)
content.BackgroundColor3 = Color3.fromRGB(15, 15, 35)
content.BorderSizePixel = 0
content.Parent = bg

local contentCorner = Instance.new("UICorner")
contentCorner.CornerRadius = UDim.new(0, 16)
contentCorner.Parent = content

local contentStroke = Instance.new("UIStroke")
contentStroke.Color = Color3.fromRGB(0, 180, 255)
contentStroke.Thickness = 2
contentStroke.Transparency = 0.4
contentStroke.Parent = content

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0.4, 0)
title.BackgroundTransparency = 1
title.Text = "Blue Electro Hub"
title.TextColor3 = Color3.fromRGB(0, 200, 255)
title.Font = Enum.Font.GothamBold
title.TextScaled = true
title.Parent = content

local subtitle = Instance.new("TextLabel")
subtitle.Size = UDim2.new(1, 0, 0.25, 0)
subtitle.Position = UDim2.new(0, 0, 0.4, 0)
subtitle.BackgroundTransparency = 1
subtitle.Text = "Verifying Files..."
subtitle.TextColor3 = Color3.fromRGB(150, 200, 255)
subtitle.Font = Enum.Font.Gotham
subtitle.TextScaled = true
subtitle.Parent = content

local barBg = Instance.new("Frame")
barBg.Size = UDim2.new(0.8, 0, 0.15, 0)
barBg.Position = UDim2.new(0.1, 0, 0.7, 0)
barBg.BackgroundColor3 = Color3.fromRGB(30, 30, 50)
barBg.BorderSizePixel = 0
barBg.Parent = content

local barBgCorner = Instance.new("UICorner")
barBgCorner.CornerRadius = UDim.new(0, 8)
barBgCorner.Parent = barBg

local barBgStroke = Instance.new("UIStroke")
barBgStroke.Color = Color3.fromRGB(0, 150, 255)
barBgStroke.Thickness = 1.5
barBgStroke.Parent = barBg

local barFill = Instance.new("Frame")
barFill.Size = UDim2.new(0, 0, 1, 0)
barFill.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
barFill.BorderSizePixel = 0
barFill.Parent = barBg

local fillCorner = Instance.new("UICorner")
fillCorner.CornerRadius = UDim.new(0, 8)
fillCorner.Parent = barFill

local tween = TweenService:Create(barFill, TweenInfo.new(2.8, Enum.EasingStyle.Quint), {Size = UDim2.new(1, 0, 1, 0)})
tween:Play()

-- ////////////  FILE CHECK  ////////////

local function checkFiles()
    local success = pcall(function()
        loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
    end)
    if success then
        subtitle.Text = "Files Verified"
        return true
    else
        subtitle.Text = "Failed to Load Rayfield"
        wait(3)
        loadingGui:Destroy()
        return false
    end
end

-- ////////////  ESP SYSTEM  ////////////

local ESPBillboards = {}

local function clearAllESP()
    for part, bill in pairs(ESPBILLboards) do
        if bill and bill.Parent then bill:Destroy() end
    end
    ESPBillboards = {}
end

local function getOreColor(oreName)
    local common = { "Iron", "Lead", "Titanium", "Tungsten", "Cobalt", "Crystal" }
    local rare = { "Viridis", "Mithril", "Purite", "Gold", "Diamond" }
    local legendary = { "Oureclasium", "Hevenite", "Hellite", "Hatrite", "Gemstone of Purity", "Forbidden Crystal", "Gemstone of Hatred", "Adamantine" }

    if table.find(legendary, oreName) then
        return Color3.fromRGB(255, 50, 50)
    elseif table.find(rare, oreName) then
        return Color3.fromRGB(50, 255, 50)
    else
        return Color3.fromRGB(50, 150, 255)
    end
end

local function createESP(part, oreName)
    if ESPBillboards[part] then return end

    local color = getOreColor(oreName)

    local bill = Instance.new("BillboardGui")
    bill.Name = "ESP_Billboard"
    bill.Size = UDim2.new(0, 100, 0, 60)
    bill.StudsOffset = Vector3.new(0, 5, 0)
    bill.Adornee = part
    bill.AlwaysOnTop = true
    bill.Parent = part

    local nameLabel = Instance.new("TextLabel")
    nameLabel.Size = UDim2.new(1, 0, 0.5, 0)
    nameLabel.BackgroundTransparency = 1
    nameLabel.Text = oreName
    nameLabel.TextColor3 = color
    nameLabel.Font = Enum.Font.Gotham
    nameLabel.TextScaled = true
    nameLabel.TextStrokeTransparency = 0.7
    nameLabel.Parent = bill

    local arrow = Instance.new("ImageLabel")
    arrow.Size = UDim2.new(0.3, 0, 0.3, 0)
    arrow.Position = UDim2.new(0.35, 0, 0.6, 0)
    arrow.BackgroundTransparency = 1
    arrow.Image = "rbxassetid://6031080047"
    arrow.ImageColor3 = color
    arrow.Parent = bill

    ESPBillboards[part] = bill
end

local function toggleSingleESP(oreName, enabled)
    clearAllESP()
    if not enabled then return end

    local found = false
    for _, model in ipairs(workspace:GetDescendants()) do
        if model:IsA("Model") and model.Name == oreName then
            found = true
            for _, part in ipairs(model:GetDescendants()) do
                if part:IsA("BasePart") then
                    createESP(part, oreName)
                end
            end
        end
    end

    if not found then
        Rayfield:Notify({
            Title = "ESP Failed",
            Content = "No '" .. oreName .. "' models found!",
            Duration = 3
        })
    end
end

local espAllActive = false
local function toggleESPAll(enabled)
    espAllActive = enabled
    clearAllESP()
    if not enabled then return end

    local oreList = {
        "Viridis","Mithril","Oureclasium","Purite","Titanium","Tungsten",
        "Lead","Iron","Hevenite","Hellite","Hatrite","Gold",
        "Gemstone of Purity","Forbidden Crystal","Gemstone of Hatred",
        "Diamond","Crystal","Cobalt","Adamantine"
    }

    local anyFound = false
    for _, oreName in ipairs(oreList) do
        for _, model in ipairs(workspace:GetDescendants()) do
            if model:IsA("Model") and model.Name == oreName then
                anyFound = true
                for _, part in ipairs(model:GetDescendants()) do
                    if part:IsA("BasePart") then
                        createESP(part, oreName)
                    end
                end
            end
        end
    end

    if not anyFound then
        Rayfield:Notify({
            Title = "ESP All Failed",
            Content = "No ore models found in workspace!",
            Duration = 4
        })
    end
end

-- ////////////  SMART AUTO-MINE WITH FULL DENIAL  ////////////

local function smartMineOre(rockPart)
    -- Check Character
    local char = player.Character
    if not char then
        Rayfield:Notify({Title = "Error", Content = "Character not loaded!", Duration = 3})
        return
    end

    -- Check Pickaxe
    local tool = char:FindFirstChild("Iron Pickaxe")
    if not tool then
        Rayfield:Notify({Title = "Error", Content = "Iron Pickaxe not equipped!", Duration = 3})
        return
    end

    -- Check Remote
    local remote = tool:FindFirstChild("RemoteFunction")
    if not remote then
        Rayfield:Notify({Title = "Error", Content = "RemoteFunction missing in pickaxe!", Duration = 3})
        return
    end

    -- Check Properties
    local properties = rockPart:FindFirstChild("Properties")
    if not properties then
        Rayfield:Notify({Title = "Error", Content = "No Properties folder in Rock!", Duration = 3})
        return
    end

    -- Check Hitpoint
    local hitpoint = properties:FindFirstChild("Hitpoint")
    if not hitpoint or not hitpoint:IsA("NumberValue") then
        Rayfield:Notify({Title = "Error", Content = "Hitpoint not found or invalid!", Duration = 3})
        return
    end

    local hitsNeeded = hitpoint.Value
    if hitsNeeded <= 0 then
        Rayfield:Notify({Title = "Already Mined", Content = "Hitpoint is 0!", Duration = 2})
        return
    end

    -- Mine exactly Hitpoint.Value times
    for i = 1, hitsNeeded do
        if not player.Character or not player.Character:FindFirstChild("HumanoidRootPart") then
            Rayfield:Notify({Title = "Stopped", Content = "You died or left!", Duration = 2})
            break
        end
        if hitpoint.Value <= 0 then
            Rayfield:Notify({Title = "Ore Broken", Content = "Mined early!", Duration = 2})
            break
        end

        local success = pcall(function()
            remote:InvokeServer("mine")
        end)

        if not success then
            Rayfield:Notify({Title = "Remote Failed", Content = "Invoke failed at hit " .. i, Duration = 3})
            break
        end

        task.wait(0.25)
    end

    Rayfield:Notify({
        Title = "Mining Complete",
        Content = "Mined " .. hitsNeeded .. " times!",
        Duration = 3
    })
end

local function teleportAndSmartMine(oreName)
    local char = player.Character or player.CharacterAdded:Wait()
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then
        Rayfield:Notify({Title = "Error", Content = "HumanoidRootPart missing!", Duration = 3})
        return
    end

    -- Find Model
    local model = nil
    for _, obj in ipairs(workspace:GetDescendants()) do
        if obj:IsA("Model") and obj.Name == oreName then
            model = obj
            break
        end
    end

    if not model then
        Rayfield:Notify({Title = "Not Found", Content = "No '" .. oreName .. "' model in workspace!", Duration = 4})
        return
    end

    -- Find Rock
    local rockPart = model:FindFirstChild("Rock")
    if not rockPart or not rockPart:IsA("BasePart") then
        Rayfield:Notify({Title = "Not Found", Content = "No 'Rock' part in " .. oreName .. "!", Duration = 4})
        return
    end

    -- Teleport
    hrp.CFrame = rockPart.CFrame + Vector3.new(0, 5, 0)
    task.wait(0.5)

    -- Mine
    smartMineOre(rockPart)
end

-- ////////////  FULLBRIGHT  ////////////

local savedLighting = {}
local fullbrightOn = false

local function setFullbright(enabled)
    if enabled and not fullbrightOn then
        savedLighting = {
            Brightness = Lighting.Brightness,
            Ambient = Lighting.Ambient,
            FogEnd = Lighting.FogEnd,
            GlobalShadows = Lighting.GlobalShadows,
            OutdoorAmbient = Lighting.OutdoorAmbient
        }
        Lighting.Brightness = 3
        Lighting.Ambient = Color3.fromRGB(255, 255, 255)
        Lighting.FogEnd = 100000
        Lighting.GlobalShadows = false
        Lighting.OutdoorAmbient = Color3.fromRGB(255, 255, 255)
        fullbrightOn = true
    elseif not enabled and fullbrightOn then
        for k, v in pairs(savedLighting) do
            Lighting[k] = v
        end
        fullbrightOn = false
    end
end

-- ////////////  SPEED & JUMP  ////////////

local function setSpeed(speed)
    local char = player.Character or player.CharacterAdded:Wait()
    local hum = char:FindFirstChildOfClass("Humanoid")
    if hum then hum.WalkSpeed = speed end
end

local function setJump(power)
    local char = player.Character or player.CharacterAdded:Wait()
    local hum = char:FindFirstChildOfClass("Humanoid")
    if hum then hum.JumpPower = power end
end

player.CharacterAdded:Connect(function(char)
    task.wait(0.1)
    local hum = char:FindFirstChildOfClass("Humanoid")
    if hum then
        hum.WalkSpeed = player:GetAttribute("SavedSpeed") or 16
        hum.JumpPower = player:GetAttribute("SavedJump") or 50
    end
end)

-- ////////////  LOAD RAYFIELD  ////////////

function loadRayfield()
    local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

    local Window = Rayfield:CreateWindow({
        Name = "Blue Electro Hub",
        LoadingTitle = "Blue Electro",
        LoadingSubtitle = "by dev",
        ConfigurationSaving = {
            Enabled = true,
            FolderName = "BlueElectroHub",
            FileName = "Config"
        },
        KeySystem = false
    })

    local MainTab = Window:CreateTab("Main", 4483362458)

    -- === FULLBRIGHT ===
    MainTab:CreateSection("Lighting")
    MainTab:CreateToggle({
        Name = "Fullbright (No Darkness)",
        CurrentValue = false,
        Callback = function(v) setFullbright(v) end
    })

    -- === ORE ESP & SMART MINE ===
    MainTab:CreateSection("Ore ESP & Smart Mining")

    local selectedOre = "Viridis"
    local mineBtn
    local espToggle
    local espAllBtn

    local oreList = {
        "Viridis","Mithril","Oureclasium","Purite","Titanium","Tungsten",
        "Lead","Iron","Hevenite","Hellite","Hatrite","Gold",
        "Gemstone of Purity","Forbidden Crystal","Gemstone of Hatred",
        "Diamond","Crystal","Cobalt","Adamantine"
    }

    local dropdown = MainTab:CreateDropdown({
        Name = "Select Ore Model",
        Options = oreList,
        CurrentOption = {"Viridis"},
        MultipleOptions = false,
        Callback = function(optionTable)
            selectedOre = optionTable[1]
            mineBtn:Set("Mine " .. selectedOre .. " (Hitpoint)")
            if espToggle.CurrentValue and not espAllActive then
                toggleSingleESP(selectedOre, true)
            end
        end
    })

    espToggle = MainTab:CreateToggle({
        Name = "ESP Selected Ore",
        CurrentValue = false,
        Callback = function(v)
            if espAllActive then
                espAllBtn:Set(false)
                espAllActive = false
            end
            toggleSingleESP(selectedOre, v)
        end
    })

    mineBtn = MainTab:CreateButton({
        Name = "Mine Viridis (Hitpoint)",
        Callback = function()
            teleportAndSmartMine(selectedOre)
        end
    })

    espAllBtn = MainTab:CreateButton({
        Name = "ESP All Ores (Color Coded)",
        Callback = function()
            local newState = not espAllActive
            espAllActive = newState
            if newState then
                espToggle:Set(false)
            end
            toggleESPAll(newState)
            espAllBtn.Name = newState and "Disable All ESP" or "ESP All Ores (Color Coded)"
        end
    })

    -- === SPEED & JUMP ===
    MainTab:CreateSection("Movement")

    local speedSlider = MainTab:CreateSlider({
        Name = "WalkSpeed",
        Range = {16, 300},
        Increment = 1,
        CurrentValue = 16,
        Suffix = " studs/s",
        Callback = function(value)
            setSpeed(value)
            player:SetAttribute("SavedSpeed", value)
        end
    })

    local jumpSlider = MainTab:CreateSlider({
        Name = "JumpPower",
        Range = {50, 300},
        Increment = 1,
        CurrentValue = 50,
        Suffix = " studs",
        Callback = function(value)
            setJump(value)
            player:SetAttribute("SavedJump", value)
        end
    })

    -- Restore saved values
    task.spawn(function()
        wait(1)
        local savedSpeed = player:GetAttribute("SavedSpeed")
        local savedJump = player:GetAttribute("SavedJump")
        if savedSpeed then speedSlider:Set(savedSpeed) end
        if savedJump then jumpSlider:Set(savedJump) end
    end)
end

-- ////////////  START  ////////////

tween.Completed:Connect(function()
    wait(0.6)
    if checkFiles() then
        subtitle.Text = "Launching Interface..."
        wait(1.2)
        loadingGui:Destroy()
        loadRayfield()
    end
end)
