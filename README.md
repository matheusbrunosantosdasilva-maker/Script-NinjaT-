--Abaixo estara o lib da nossa UI-- 


local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/7yhx/kwargs_Ui_Library/main/source.lua"))()

local UI = Lib:Create{
   Theme = "Dark", -- or any other theme
   Size = UDim2.new(0, 555, 0, 400) -- default
}

local Main = UI:Tab{
   Name = "inicio"
}

local Divider = Main:Divider{
   Name = "Inicio shit"
}

local QuitDivider = Main:Divider{
   Name = "Sair"
}
local KillAll = Divider:Button{
   Name = "ESP",
   Description = "ESP ATIVADO",
   Callback = function ESP(PLAYER)
 local function updateESP()
	for _, p in pairs(Players:GetPlayers()) do
		if p ~= player and p.Character and p.Character:FindFirstChild("Head") then
			if not espLabels[p] then
				local label = createLabel(p.Name)
				espLabels[p] = label
			end
			local head = p.Character.Head
			local pos, onScreen = camera:WorldToViewportPoint(head.Position)
			local label = espLabels[p]
			if onScreen and espEnabled then
				label.Position = UDim2.new(0, pos.X - 100, 0, pos.Y - 12)
				label.Visible = true
			else
				label.Visible = false
	   end     
   end
}
local LoopKillAll = Divider:Toggle{
   Name = "FOV ESP",
   Description = "FOV ESP ATIVADO.",
   Callback = function FOV(BRAINROT)
 local function highlightValuableBrainrot()
	if not fovEnabled then return end
	local best = nil
	local highestValue = 0
	for _, obj in pairs(workspace:GetChildren()) do
		if obj:IsA("Model") and obj:FindFirstChild("BrainrotValue") then
			local value = obj.BrainrotValue.Value
			if value > highestValue then
				highestValue = value
				best = obj
			end
		end    
}
local Function DisableESP()
if input.KeyCode == Enum.KeyCode.F1 then
		speedEnabled = not speedEnabled
		humanoid.WalkSpeed = speedEnabled and boostedSpeed or normalSpeed
	elseif input.KeyCode.F2 then
		jumpEnabled = not jumpEnabled
		humanoid.JumpPower = jumpEnabled and boostedJump or normalJump
	elseif input.KeyCode.F3 then
		espEnabled = not espEnabled
	elseif input.KeyCode.F4 then
		fovEnabled = not fovEnabled
	end
end
}

ESP (Players)
FOV (BRAINROT)

Divider:ColorPicker{
   Name = "ESP color",
   Default = Color3.fromRGB(0, 255, 255), -- default,
   Callback = function(Value)
       print(Value)
   end
}

-- Serviços
local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local camera = workspace.CurrentCamera

-- Configurações
local speedEnabled = false
local jumpEnabled = false
local espEnabled = false
local fovEnabled = false

local normalSpeed = 16
local boostedSpeed = 50
local normalJump = 50
local boostedJump = 66
