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




sec:Button("Script Hub do Shadow", function()
 SolarisLib:Notification("Shadow Hub", "Sucesso")
end)
