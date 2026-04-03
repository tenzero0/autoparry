--[[
	WARNING: Heads up! This script has not been verified by ScriptBlox. Use at your own risk!
]]
-- start pack
local player = game.Players.LocalPlayer
local UIS = game:GetService("UserInputService")

-- UI
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "TeleportUI"
screenGui.ResetOnSpawn = false
screenGui.Parent = player:WaitForChild("PlayerGui")

-- ss
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 220, 0, 120)
frame.Position = UDim2.new(0.4, 0, 0.4, 0)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.Active = true
frame.Draggable = true
frame.Visible = true
frame.Parent = screenGui

-- ss
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 30)
title.Text = "BlinkCore"
title.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Parent = frame

-- sss
local button = Instance.new("TextButton")
button.Size = UDim2.new(1, -20, 0, 40)
button.Position = UDim2.new(0, 10, 0.5, -10)
button.Text = "START TP"
button.BackgroundColor3 = Color3.fromRGB(70, 130, 180)
button.TextColor3 = Color3.fromRGB(255, 255, 255)
button.Parent = frame

-- ss
local autoTP = false
local currentCharacter = nil

-- ss
local function updateCharacter(char)
    currentCharacter = char
end

player.CharacterAdded:Connect(updateCharacter)
if player.Character then
    updateCharacter(player.Character)
end

-- tp
local function teleportPlayer()
    if currentCharacter and currentCharacter:FindFirstChild("HumanoidRootPart") then
        currentCharacter.HumanoidRootPart.CFrame = CFrame.new(200, 200, 200)
    end
end

-- autio
task.spawn(function()
    while true do
        if autoTP then
            teleportPlayer()
        end
        task.wait(1)
    end
end)

-- ss
button.MouseButton1Click:Connect(function()
    autoTP = not autoTP
    
    if autoTP then
        button.Text = "STOP TP"
        button.BackgroundColor3 = Color3.fromRGB(200, 70, 70)
    else
        button.Text = "START TP"
        button.BackgroundColor3 = Color3.fromRGB(70, 130, 180)
    end
end)

-- ss
UIS.InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then return end
    
    if input.KeyCode == Enum.KeyCode.Insert then
        frame.Visible = not frame.Visible
    end
end)
