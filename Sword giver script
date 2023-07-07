--!strict
local box = script.parent
local box2 = game.Workspace.RemoveSword

function giveSword (bodyPart)
	local partParent = bodyPart.parent
	local player = game.Players:GetPlayerFromCharacter(partParent)
	local Humanoid = partParent:FindFirstChild("Humanoid")
	if player ~= nil and Humanoid ~= nil then
		local backpack = player:FindFirstChild("Backpack")
		--Check that the sword is not in backpack or held by character
		if not backpack:FindFirstChild("ClassicSword") and not partParent:FindFirstChild("ClassicSword") then
			local sword = game.ServerStorage:FindFirstChild("ClassicSword")
			local clone = sword:clone()
			clone.Parent = backpack
			print("Sword given")
			Humanoid:EquipTool(backpack:FindFirstChild("ClassicSword"))
		end
	end
end

box.Touched:Connect(giveSword)

function removeSword (bodyPart)
	local partParent = bodyPart.parent
	local Humanoid = partParent:FindFirstChild("Humanoid")
	if Humanoid ~= nil then
		local backpack = game.Players:GetPlayerFromCharacter(partParent).Backpack
		--Check both baclpack and humanoid for classicsword
		local sword = backpack:FindFirstChild("ClassicSword") or partParent:FindFirstChild("ClassicSword")
		if sword ~= nil then
			Humanoid:UnequipTools()
			sword:Destroy()
			print("Sword removed")
		end
	end
end

box2.Touched:Connect(removeSword)
