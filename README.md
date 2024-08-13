local Library = loadstring(game:HttpGet("https://pastebin.com/raw/vff1bQ9F"))()
local Window = Library.CreateLib("Made By SaymonDipz", "Midnight")
local Tab = Window:NewTab("Chams esp")
local Section = Tab:NewSection("Chams")
Section:NewButton("Chams", "Chams", function()
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local RunService = game:GetService("RunService")

local Settings = {
    ESP_Enabled = true,
    ESP_TeamCheck = false,
    Chams = true,
    Chams_Color = Color3.fromRGB(0, 0, 255),
    Chams_Transparency = 0.9,
    Chams_Glow_Color = Color3.fromRGB(255, 0, 0),
    Glow_Transparency = 0.3
}

local function DestroyChams(character)
    for _, part in ipairs(character:GetChildren()) do
        if part:IsA("BasePart") and part.Transparency ~= 1 then
            local glow = part:FindFirstChild("Glow")
            local chams = part:FindFirstChild("Chams")

            if glow then glow:Destroy() end
            if chams then chams:Destroy() end
        end
    end
end

RunService.Heartbeat:Connect(function()
    if Settings.ESP_Enabled then
        for _, player in ipairs(Players:GetPlayers()) do
            if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                local humanoid = player.Character:FindFirstChild("Humanoid")
                if humanoid and humanoid.Health > 0 then
                    if not (Settings.ESP_TeamCheck and player.Team == LocalPlayer.Team) then
                        local character = player.Character

                        for _, part in ipairs(character:GetChildren()) do
                            if part:IsA("BasePart") and part.Transparency ~= 1 then
                                if Settings.Chams then
                                    if not part:FindFirstChild("Glow") and not part:FindFirstChild("Chams") then
                                        local chamsBox = Instance.new("BoxHandleAdornment", part)
                                        chamsBox.Name = "Chams"
                                        chamsBox.AlwaysOnTop = true
                                        chamsBox.ZIndex = 4
                                        chamsBox.Adornee = part
                                        chamsBox.Color3 = Settings.Chams_Color
                                        chamsBox.Transparency = Settings.Chams_Transparency
                                        chamsBox.Size = part.Size + Vector3.new(0.02, 0.02, 0.02)

                                        local glowBox = Instance.new("BoxHandleAdornment", part)
                                        glowBox.Name = "Glow"
                                        glowBox.AlwaysOnTop = false
                                        glowBox.ZIndex = 3
                                        glowBox.Adornee = part
                                        glowBox.Color3 = Settings.Chams_Glow_Color
                                        glowBox.Size = chamsBox.Size + Vector3.new(0.13, 0.13, 0.13)
                                        glowBox.Transparency = Settings.Glow_Transparency
                                    end
                                else
                                    DestroyChams(character)
                                end
                            end
                        end
                    else
                        DestroyChams(player.Character)
                    end
                else
                    DestroyChams(player.Character)
                end
            end
        end
    else
        for _, player in ipairs(Players:GetPlayers()) do
            if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                local humanoid = player.Character:FindFirstChild("Humanoid")
                if humanoid and humanoid.Health > 0 then
                    DestroyChams(player.Character)
                end
            end
        end
    end
end)
    print("Clicked")
end)
local Tab = Window:NewTab("Meme sea")
local Section = Tab:NewSection("Meme sea")
Section:NewButton("Elgato hub", "Elgato hub", function()
loadstring(game:HttpGet(('https://raw.githubusercontent.com/FrostLua/Krakles/main/ElgatoHub/Loader.lua'),true))()
    print("Clicked")
end)
local Tab = Window:NewTab("Race clicker")
local Section = Tab:NewSection("Race clicker")
Section:NewButton("Tbao hub", "Tbao hub", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/tbao143/thaibao/main/TbaoHubRaceClicker"))()
    print("Clicked")
end)
local Tab = Window:NewTab("Evade")
local Section = Tab:NewSection("Evade")
Section:NewButton("Darkrai X", "Darkrai X", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/GamingScripter/Darkrai-X/main/Games/Evade"))()  
    print("Clicked")
end)
local Tab = Window:NewTab("Universal Scripts")
local Section = Tab:NewSection("Universal Scripts")
Section:NewButton("Ghost hub", "Ghost hub", function()
loadstring(game:HttpGet('https://raw.githubusercontent.com/GhostPlayer352/Test4/main/GhostHub'))()  
    print("Clicked")
end)
local Tab = Window:NewTab("Keybinds")
local Section = Tab:NewSection("Keybinds")
Section:NewKeybind("Close and open UI", "Close and open UI", Enum.KeyCode.F, function()
	Library:ToggleUI()
end)
