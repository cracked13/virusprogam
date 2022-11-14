local SolarisLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/sol"))()

--[[SolarisLib:New({
  Name - Title of the UI <string>
  FolderToSave - Name of the folder where the UI files will be stored <string>
})]]
local win = SolarisLib:New({
  Name = "Shadow Hub",
  FolderToSave = "ShadowHubstuf"
})

--win:Tab(title <string>)
local tab = win:Tab("Tab 1")

--tab:Section(title <string>)
local sec = tab:Section("Elements")


--sec:Button(title <string>, callback <function>)
sec:Button("Nova Anti Reap", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/darckgames0103/ANTINOVA/main/README.md"))()
  SolarisLib:Notification("Shadow Hub", "Voce escolheu novo anti reap")
end)



--[[
toggle:Set(state <boolean>)
]]

--sec:Slider(title <string>,default <number>,max <number>,minimum <number>,increment <number>, flag <string>, callback <function>)
local slider = sec:Slider("Slider", 0,25,0,2.5,"Slider", function(t)
  print(t)
end)






sec:Textbox("buy custom", true, function(t)
_G.custombuy = t
end)
sec:Textbox("buy Custom Number", true, function(t)
for i = 1,t do
		wait(0.01)
		game:GetService("ReplicatedStorage").RemoteEvents.BuyItemCash:FireServer(_G.custombuy)
	end
end)

sec:Textbox("buy the banana", true, function(t)
 for i = 1,t do
		wait(0.01)
		game:GetService("ReplicatedStorage").RemoteEvents.BuyItemCash:FireServer("The banana")
	end
end)

sec:Textbox("Drop Custom Item (x15)", true, function(t)
_G.dropcustom = txt
	for i = 1,15 do
		game:GetService("ReplicatedStorage").RemoteEvents.Equip:FireServer(_G.dropcustom)
		wait(0.35)
		game:GetService("ReplicatedStorage").RemoteEvents.Drop:FireServer(_G.dropcustom)
		wait(0.35)
	end
end)


sec:Button("Night Mode ", function()
local Info = TweenInfo.new(3, Enum.EasingStyle.Exponential)
	if game:GetService("Players").LocalPlayer:GetAttribute("IsDay") then
		game:GetService("TweenService"):Create(game:GetService("Lighting"), Info, {ClockTime = 12}):Play()
		game:GetService("Players").LocalPlayer:SetAttribute("IsDay", false)
	else
		game:GetService("TweenService"):Create(game:GetService("Lighting"), Info, {ClockTime = 0}):Play()
		game:GetService("Players").LocalPlayer:SetAttribute("IsDay", true)
	end

  
end)

sec:Button("Inf Jump ", function()
_G.infinjump = true
	local Player = game:GetService("Players").LocalPlayer
	local Mouse = Player:GetMouse()
	Mouse.KeyDown:connect(function(k)
		if _G.infinjump then
			if k:byte() == 32 then
				Humanoid = game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
				Humanoid:ChangeState("Jumping")
				wait(0.1)
				Humanoid:ChangeState("Seated")
			end
		end
	end)
end)

sec:Button("G to Fly ", function()



local players = game:GetService("Players")
	local lp = players.LocalPlayer
	local Mouses = lp:GetMouse()
	mouse = Mouses
	local workspace = game.Workspace
	function sFLY(vfly)
		FLYING = false
		speedofthefly = 1.5
		speedofthevfly = 1
		while not lp or not lp.Character or not lp.Character:FindFirstChild('HumanoidRootPart') or not lp.Character:FindFirstChild('Humanoid') or not mouse do
			wait()
		end 
		local T = lp.Character.HumanoidRootPart
		local CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
		local lCONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
		local SPEED = 0
		local function FLY()
			FLYING = true
			local BG = Instance.new('BodyGyro', T)
			local BV = Instance.new('BodyVelocity', T)
			BG.P = 9e4
			BG.maxTorque = Vector3.new(9e9, 9e9, 9e9)
			BG.cframe = T.CFrame
			BV.velocity = Vector3.new(0, 0, 0)
			BV.maxForce = Vector3.new(9e9, 9e9, 9e9)
			spawn(function()
				while FLYING do
					if not vfly then
						lp.Character:FindFirstChild("Humanoid").PlatformStand = true
					end
					if CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0 then
						SPEED = 50
					elseif not (CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0) and SPEED ~= 0 then
						SPEED = 0
					end
					if (CONTROL.L + CONTROL.R) ~= 0 or (CONTROL.F + CONTROL.B) ~= 0 or (CONTROL.Q + CONTROL.E) ~= 0 then
						BV.velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (CONTROL.F + CONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(CONTROL.L + CONTROL.R, (CONTROL.F + CONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
						lCONTROL = {F = CONTROL.F, B = CONTROL.B, L = CONTROL.L, R = CONTROL.R}
					elseif (CONTROL.L + CONTROL.R) == 0 and (CONTROL.F + CONTROL.B) == 0 and (CONTROL.Q + CONTROL.E) == 0 and SPEED ~= 0 then
						BV.velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (lCONTROL.F + lCONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(lCONTROL.L + lCONTROL.R, (lCONTROL.F + lCONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
					else
						BV.velocity = Vector3.new(0, 0, 0)
					end
					BG.cframe = workspace.CurrentCamera.CoordinateFrame
					wait()
				end
				CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
				lCONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
				SPEED = 0
				BG:destroy()
				BV:destroy()
				lp.Character.Humanoid.PlatformStand = false
			end)
		end
		mouse.KeyDown:connect(function(KEY)
			if KEY:lower() == 'w' then
				if vfly then
					CONTROL.F = speedofthevfly
				else
					CONTROL.F = speedofthefly
				end
			elseif KEY:lower() == 's' then
				if vfly then
					CONTROL.B = - speedofthevfly
				else
					CONTROL.B = - speedofthefly
				end
			elseif KEY:lower() == 'a' then
				if vfly then
					CONTROL.L = - speedofthevfly
				else
					CONTROL.L = - speedofthefly
				end
			elseif KEY:lower() == 'd' then
				if vfly then
					CONTROL.R = speedofthevfly
				else
					CONTROL.R = speedofthefly
				end
			elseif KEY:lower() == 'y' then
				if vfly then
					CONTROL.Q = speedofthevfly*2
				else
					CONTROL.Q = speedofthefly*2
				end
			elseif KEY:lower() == 't' then
				if vfly then
					CONTROL.E = -speedofthevfly*2
				else
					CONTROL.E = -speedofthefly*2
				end
			end
		end)
		mouse.KeyUp:connect(function(KEY)
			if KEY:lower() == 'w' then
				CONTROL.F = 0
			elseif KEY:lower() == 's' then
				CONTROL.B = 0
			elseif KEY:lower() == 'a' then
				CONTROL.L = 0
			elseif KEY:lower() == 'd' then
				CONTROL.R = 0
			elseif KEY:lower() == 'y' then
				CONTROL.Q = 0
			elseif KEY:lower() == 't' then
				CONTROL.E = 0
			end
		end)
		FLY()
	end

	mouse.KeyDown:connect(function(KEY)
		if KEY:lower() == 'g' then
			if FLYING == false then
				sFLY()
			else
				FLYING = false
				lp.Character.Humanoid.PlatformStand = false
			end
		end
	end)
end)



