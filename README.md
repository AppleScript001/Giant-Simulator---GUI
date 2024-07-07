local Library = loadstring(game:HttpGet("https://pastebin.com/raw/KNBp0LRy"), "Coastified UI")()
repeat wait() until game:IsLoaded()
game:GetService("Players").LocalPlayer.Idled:connect(function()
game:GetService("VirtualUser"):ClickButton2(Vector2.new())
end)
local Window = Library:NewWindow("Giant Simulator")
local Section = Window:NewSection("AutoFarm")
local Toggle = Section:CreateToggle("Auto [Power]", function(Value)
_G.Power = Value
while _G.Power do
wait(0.1)  -- Wait for 1 second before checking for enemies
local toolName = "Weight" -- Replace "YourToolNameHere" with the name of your tool 
local LocalPlayer = game:GetService("Players").LocalPlayer
for i, v in pairs(LocalPlayer.Backpack:GetChildren()) do
if v:IsA('Tool') and v.Name == toolName then
    v.Parent = LocalPlayer.Character
    break -- Stop the loop after picking up the tool
end
end
local args = {
    [1] = math.huge
}

game:GetService("Players").LocalPlayer.Character.Weight.Event:FireServer(unpack(args))
end
end)
local Section = Window:NewSection("GiveAll")
local Toggle = Section:CreateToggle("Give [9B Power]", function(Value)
_G.B = Value
while _G.B do
wait(0.1)  -- Wait for 1 second before checking for enemies
game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("ClaimReward"):FireServer("Power", 9999999999)
end
end)
local Toggle = Section:CreateToggle("Give [Potion x5 INF]", function(Value)
_G.Potion = Value
while _G.Potion do
wait(0.1)  -- Wait for 1 second before checking for enemies
game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("AddWheelSpinValue"):FireServer("x5 Power", math.huge)
end
end)
local Button = Section:CreateButton("Give [WheelSpins INF]", function()
for i = 1, 500 do
game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("ClaimReward"):FireServer("Spins", 100)
end
end)
local Button = Section:CreateButton("Give Pet [Fire Hydra x5]", function()
    local args = {
        [1] = "Limited",
        [2] = "Fire Hydra"
    }
    
    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("HatchPet"):InvokeServer(unpack(args))
end)
