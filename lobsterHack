local UserInputService = game:GetService("UserInputService")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")
local flying = false
local anchor = false
local sp = false
local flySpeed = 50
local storSP
local storJP

-- Create a ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "AdminPanel"
screenGui.Parent = PlayerGui

-- Create a Frame for the admin panel
local adminFrame = Instance.new("Frame")
adminFrame.Size = UDim2.new(0, 250, 0, 400)
adminFrame.Position = UDim2.new(0.35, 0, 0.3, 0)
adminFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
adminFrame.Parent = screenGui

local UiDr = Instance.new("UIDragDetector")
UiDr.Parent = adminFrame

-- Create a title label
local titleLabel = Instance.new("TextLabel")
titleLabel.Size = UDim2.new(1, 0, 0, 50)
titleLabel.Position = UDim2.new(0, 0, 0, 0)
titleLabel.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
titleLabel.Text = "Lobster Hack"
titleLabel.TextScaled = true
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.Parent = adminFrame

-- Create a sample button
local sampleButton = Instance.new("TextButton")
sampleButton.Size = UDim2.new(0.8, 0, 0, 50)
sampleButton.Position = UDim2.new(0.1, 0, 0, 60)
sampleButton.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
sampleButton.Text = "Fly"
sampleButton.TextScaled = true
sampleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
sampleButton.Parent = adminFrame

local sampleButton2 = Instance.new("TextButton")
sampleButton2.Size = UDim2.new(0.8, 0, 0, 50)
sampleButton2.Position = UDim2.new(0.1, 0, 0, 120)
sampleButton2.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
sampleButton2.Text = "Anchor"
sampleButton2.TextScaled = true
sampleButton2.TextColor3 = Color3.fromRGB(255, 255, 255)
sampleButton2.Parent = adminFrame

local sampleButton3 = Instance.new("TextButton")
sampleButton3.Size = UDim2.new(0.8, 0, 0, 50)
sampleButton3.Position = UDim2.new(0.1, 0, 0, 180)
sampleButton3.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
sampleButton3.Text = "Speed"
sampleButton3.TextScaled = true
sampleButton3.TextColor3 = Color3.fromRGB(255, 255, 255)
sampleButton3.Parent = adminFrame

sampleButton.Activated:Connect(function()
	local char = LocalPlayer.Character
	flying = not flying
	if flying then
		sampleButton.BackgroundColor3 = Color3.new(0.282353, 1, 0.0627451)
		local bodyVelocity = Instance.new("BodyVelocity")
		bodyVelocity.MaxForce = Vector3.new(4000, 4000, 4000)
		bodyVelocity.Velocity = Vector3.new(0, 0, 0)
		bodyVelocity.Parent = char:WaitForChild("HumanoidRootPart")
	else
		sampleButton.BackgroundColor3 = Color3.new(1, 0, 0.0156863)
		char:WaitForChild("HumanoidRootPart"):FindFirstChild("BodyVelocity"):Destroy()
	end
end)
sampleButton2.Activated:Connect(function()
	local char = LocalPlayer.Character
	anchor = not anchor
	if anchor then
		sampleButton2.BackgroundColor3 = Color3.new(0.282353, 1, 0.0627451)
	else
		sampleButton2.BackgroundColor3 = Color3.new(1, 0, 0.0156863)
	end
	if char:FindFirstChild("Torso") then
		char:FindFirstChild("Torso").Anchored = anchor
	elseif char:FindFirstChild("LowerTorso") then
		char:FindFirstChild("LowerTorso").Anchored = anchor
	end
end)
sampleButton3.Activated:Connect(function()
	local char = LocalPlayer.Character
	sp = not sp
	if sp then
		storSP = char:FindFirstChild("Humanoid").WalkSpeed 
		storJP = char:FindFirstChild("Humanoid").JumpPower 
		char:FindFirstChild("Humanoid").WalkSpeed = 64
		char:FindFirstChild("Humanoid").JumpPower = 100
		sampleButton3.BackgroundColor3 = Color3.new(0.282353, 1, 0.0627451)
	else
		char:FindFirstChild("Humanoid").WalkSpeed = storSP
		char:FindFirstChild("Humanoid").JumpPower = storJP
		sampleButton3.BackgroundColor3 = Color3.new(1, 0, 0.0156863)
	end
end)
game:GetService("RunService").RenderStepped:Connect(function()
	if flying then
		local camera = workspace.CurrentCamera
		local direction = Vector3.new()

		if UserInputService:IsKeyDown(Enum.KeyCode.W) then
			direction = direction + camera.CFrame.LookVector
		end
		if UserInputService:IsKeyDown(Enum.KeyCode.S) then
			direction = direction - camera.CFrame.LookVector
		end
		if UserInputService:IsKeyDown(Enum.KeyCode.A) then
			direction = direction - camera.CFrame.RightVector
		end
		if UserInputService:IsKeyDown(Enum.KeyCode.D) then
			direction = direction + camera.CFrame.RightVector
		end

		LocalPlayer.Character:WaitForChild("HumanoidRootPart"):FindFirstChild("BodyVelocity").Velocity = direction * flySpeed
	end
end)
