-- Valex Speed Changer v2.1 (With Close Button)
local player = game.Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ValexSpeedUI"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

-- Main Frame
local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 320, 0, 220)
mainFrame.Position = UDim2.new(0.5, -160, 0.5, -110)
mainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
mainFrame.BorderSizePixel = 0
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = screenGui

Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0, 12)

-- Title
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, -50, 0, 50)
title.Position = UDim2.new(0, 10, 0, 0)
title.BackgroundTransparency = 1
title.Text = "Valex Speed Changer"
title.TextColor3 = Color3.fromRGB(0, 170, 255)
title.TextScaled = true
title.Font = Enum.Font.GothamBold
title.TextXAlignment = Enum.TextXAlignment.Left
title.Parent = mainFrame

-- Close Button (X)
local closeBtn = Instance.new("TextButton")
closeBtn.Size = UDim2.new(0, 40, 0, 40)
closeBtn.Position = UDim2.new(1, -40, 0, 0)
closeBtn.BackgroundTransparency = 1
closeBtn.Text = "✕"
closeBtn.TextColor3 = Color3.fromRGB(255, 80, 80)
closeBtn.TextScaled = true
closeBtn.Font = Enum.Font.GothamBold
closeBtn.Parent = mainFrame

-- Speed Input
local speedBox = Instance.new("TextBox")
speedBox.Size = UDim2.new(0.7, 0, 0, 40)
speedBox.Position = UDim2.new(0.15, 0, 0.35, 0)
speedBox.PlaceholderText = "Enter Speed"
speedBox.Text = "60"
speedBox.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
speedBox.TextColor3 = Color3.fromRGB(255, 255, 255)
speedBox.Font = Enum.Font.Gotham
speedBox.TextScaled = true
speedBox.Parent = mainFrame
Instance.new("UICorner", speedBox).CornerRadius = UDim.new(0, 8)

-- Apply Button
local applyBtn = Instance.new("TextButton")
applyBtn.Size = UDim2.new(0.45, 0, 0, 45)
applyBtn.Position = UDim2.new(0.05, 0, 0.65, 0)
applyBtn.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
applyBtn.Text = "Apply"
applyBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
applyBtn.Font = Enum.Font.GothamBold
applyBtn.TextScaled = true
applyBtn.Parent = mainFrame
Instance.new("UICorner", applyBtn).CornerRadius = UDim.new(0, 10)

-- Toggle Button
local toggleBtn = Instance.new("TextButton")
toggleBtn.Size = UDim2.new(0.45, 0, 0, 45)
toggleBtn.Position = UDim2.new(0.5, 0, 0.65, 0)
toggleBtn.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
toggleBtn.Text = "ON"
toggleBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleBtn.Font = Enum.Font.GothamBold
toggleBtn.TextScaled = true
toggleBtn.Parent = mainFrame
Instance.new("UICorner", toggleBtn).CornerRadius = UDim.new(0, 10)

-- Variables
local humanoid = nil
local currentSpeed = 60
local enabled = true
local NORMAL_SPEED = 16

local function updateHumanoid()
    if player.Character then
        humanoid = player.Character:FindFirstChild("Humanoid")
    end
end

local function setSpeed(speed)
    updateHumanoid()
    if humanoid then
        humanoid.WalkSpeed = speed
    end
end

-- Apply
applyBtn.MouseButton1Click:Connect(function()
    local num = tonumber(speedBox.Text)
    if num and num > 0 then
        currentSpeed = num
        if enabled then
            setSpeed(currentSpeed)
        end
    else
        speedBox.Text = tostring(currentSpeed)
    end
end)

-- Toggle
toggleBtn.MouseButton1Click:Connect(function()
    enabled = not enabled
    if enabled then
        toggleBtn.Text = "ON"
        toggleBtn.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
        setSpeed(currentSpeed)
    else
        toggleBtn.Text = "OFF"
        toggleBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
        setSpeed(NORMAL_SPEED)
    end
end)

-- Close Button
closeBtn.MouseButton1Click:Connect(function()
    screenGui:Destroy()
end)

-- Respawn Handler
player.CharacterAdded:Connect(function()
    task.wait(0.6)
    updateHumanoid()
    if enabled then
        setSpeed(currentSpeed)
    else
        setSpeed(NORMAL_SPEED)
    end
end)

-- Initial
updateHumanoid()
if humanoid then
    setSpeed(currentSpeed)
end

print("✅ Valex Speed Changer Loaded")
