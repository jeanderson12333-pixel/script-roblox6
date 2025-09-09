# script-roblox6
hujokils
-- LocalScript no StarterPlayer > StarterPlayerScripts
-- Permite voar com a tecla F

local flying = false
local UIS = game:GetService("UserInputService")
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local root = character:WaitForChild("HumanoidRootPart")
local bodyGyro = Instance.new("BodyGyro")
local bodyVelocity = Instance.new("BodyVelocity")

UIS.InputBegan:Connect(function(input)
	if input.KeyCode == Enum.KeyCode.F then
		flying = not flying
		if flying then
			bodyGyro.Parent = root
			bodyVelocity.Parent = root
			bodyGyro.MaxTorque = Vector3.new(400000, 400000, 400000)
			bodyVelocity.MaxForce = Vector3.new(400000, 400000, 400000)
			while flying do
				bodyGyro.CFrame = workspace.CurrentCamera.CFrame
				bodyVelocity.Velocity = workspace.CurrentCamera.CFrame.lookVector * 50
				wait()
			end
		else
			bodyGyro:Destroy()
			bodyVelocity:Destroy()
		end
	end
end)
