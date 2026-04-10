-- SALTO INFINITO - Versão Leve para Loadstring

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")

local player = Players.LocalPlayer
local infiniteJumpEnabled = false
local isMinimized = false

-- Remove menu antigo
local old = player:FindFirstChild("PlayerGui") and player.PlayerGui:FindFirstChild("InfJumpMenu")
if old then old:Destroy() end

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "InfJumpMenu"
screenGui.ResetOnSpawn = false
screenGui.Parent = player:WaitForChild("PlayerGui")

local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 240, 0, 140)
mainFrame.Position = UDim2.new(0.5, -120, 0.35, 0)
mainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = screenGui

Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0, 12)

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, -65, 0, 35)
title.Position = UDim2.new(0, 10, 0, 0)
title.BackgroundTransparency = 1
title.Text = "Salto Infinito"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.TextScaled = true
title.Font = Enum.Font.GothamBold
title.TextXAlignment = Enum.TextXAlignment.Left
title.Parent = mainFrame

local minBtn = Instance.new("TextButton")
minBtn.Size = UDim2.new(0, 28, 0, 28)
minBtn.Position = UDim2.new(1, -60, 0, 4)
minBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
minBtn.Text = "–"
minBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
minBtn.TextScaled = true
minBtn.Font = Enum.Font.GothamBold
minBtn.Parent = mainFrame
Instance.new("UICorner", minBtn).CornerRadius = UDim.new(0, 6)

local closeBtn = Instance.new("TextButton")
closeBtn.Size = UDim2.new(0, 28, 0, 28)
closeBtn.Position = UDim2.new(1, -30, 0, 4)
closeBtn.BackgroundColor3 = Color3.fromRGB(190, 40, 40)
closeBtn.Text = "X"
closeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
closeBtn.TextScaled = true
closeBtn.Font = Enum.Font.GothamBold
closeBtn.Parent = mainFrame
Instance.new("UICorner", closeBtn).CornerRadius = UDim.new(0, 6)

local toggleBtn = Instance.new("TextButton")
toggleBtn.Size = UDim2.new(0.88, 0, 0, 55)
toggleBtn.Position = UDim2.new(0.06, 0, 0.38, 0)
toggleBtn.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
toggleBtn.Text = "ATIVAR SALTO INFINITO"
toggleBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleBtn.TextScaled = true
toggleBtn.Font = Enum.Font.GothamSemibold
toggleBtn.Parent = mainFrame
Instance.new("UICorner", toggleBtn).CornerRadius = UDim.new(0, 10)

local statusLabel = Instance.new("TextLabel")
statusLabel.Size = UDim2.new(1, 0, 0, 20)
statusLabel.Position = UDim2.new(0, 0, 1, -25)
statusLabel.BackgroundTransparency = 1
statusLabel.Text = "Desligado"
statusLabel.TextColor3 = Color3.fromRGB(255, 70, 70)
statusLabel.TextScaled = true
statusLabel.Font = Enum.Font.Gotham
statusLabel.Parent = mainFrame

local normalSize = UDim2.new(0, 240, 0, 140)
local miniSize = UDim2.new(0, 240, 0, 40)

local function updateToggle()
	if infiniteJumpEnabled then
		toggleBtn.BackgroundColor3 = Color3.fromRGB(0, 160, 0)
		toggleBtn.Text = "SALTO INFINITO: LIGADO"
		statusLabel.Text = "Ligado"
		statusLabel.TextColor3 = Color3.fromRGB(0, 255, 80)
	else
		toggleBtn.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
		toggleBtn.Text = "ATIVAR SALTO INFINITO"
		statusLabel.Text = "Desligado"
		statusLabel.TextColor3 = Color3.fromRGB(255, 70, 70)
	end
end

local function toggleMinimize()
	isMinimized = not isMinimized
	if isMinimized then
		mainFrame:TweenSize(miniSize, "Out", "Quad", 0.2, true)
		toggleBtn.Visible = false
		statusLabel.Visible = false
		minBtn.Text = "+"
	else
		mainFrame:TweenSize(normalSize, "Out", "Quad", 0.2, true)
		toggleBtn.Visible = true
		statusLabel.Visible = true
		minBtn.Text = "–"
	end
end

UserInputService.JumpRequest:Connect(function()
	if not infiniteJumpEnabled then return end
	local char = player.Character
	if char then
		local hum = char:FindFirstChild("Humanoid")
		if hum then
			hum:ChangeState(Enum.HumanoidStateType.Jumping)
		end
	end
end)

toggleBtn.MouseButton1Click:Connect(function()
	infiniteJumpEnabled = not infiniteJumpEnabled
	updateToggle()
end)

minBtn.MouseButton1Click:Connect(toggleMinimize)

closeBtn.MouseButton1Click:Connect(function()
	screenGui:Destroy()
end)

updateToggle()
print("✅ Salto Infinito carregado via Loadstring!")
