placeid = 2788229376
if game.PlaceId == placeid then
    local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
    local Window = Library.CreateLib("[Doge Hub] Da hood", "BloodTheme")

    -- Main
    local Main = Window:NewTab("Scripts")
    local MainSection = Main:NewSection("Scripts")

    MainSection:NewButton("Fly", "Allows you to fly", function(v)
wait(.30) local A_1 = "[Doge Hub] Fly enabled." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2)
local plr = game.Players.LocalPlayer
local mouse = plr:GetMouse()
local Humanoid = game.Players.LocalPlayer.Character.Humanoid or game.Players.LocalPlayer.Character.humanoid  

		localplayer = plr
		
		if workspace:FindFirstChild("Core") then
			workspace.Core:Destroy()
		end
		
		local Core = Instance.new("Part")
		Core.Name = "Core"
		Core.Size = Vector3.new(0.05, 0.05, 0.05)

		spawn(function()
			Core.Parent = workspace
			local Weld = Instance.new("Weld", Core)
			Weld.Part0 = Core
			Weld.Part1 = localplayer.Character.LowerTorso
			Weld.C0 = CFrame.new(0, 0, 0)
		end)
		
		workspace:WaitForChild("Core")
		
		local torso = workspace.Core
		flying = true
		local speed=10
		local keys={a=false,d=false,w=false,s=false} 
		local e1
		local e2
		local function start()
			local pos = Instance.new("BodyPosition",torso)
			local gyro = Instance.new("BodyGyro",torso)
			pos.Name="EPIXPOS"
			pos.maxForce = Vector3.new(math.huge, math.huge, math.huge)
			pos.position = torso.Position
			gyro.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
			gyro.cframe = torso.CFrame
			repeat
				wait()
				Humanoid.PlatformStand=true
				local new=gyro.cframe - gyro.cframe.p + pos.position
				if not keys.w and not keys.s and not keys.a and not keys.d then
					speed=5
				end
				if keys.w then 
					new = new + workspace.CurrentCamera.CoordinateFrame.lookVector * speed
					speed=speed+0
				end
				if keys.s then 
					new = new - workspace.CurrentCamera.CoordinateFrame.lookVector * speed
					speed=speed+0
				end
				if keys.d then 
					new = new * CFrame.new(speed,0,0)
					speed=speed+0
				end
				if keys.a then 
					new = new * CFrame.new(-speed,0,0)
					speed=speed+0
				end
				if speed>10 then
					speed=5
				end
				pos.position=new.p
				if keys.w then
					gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(-math.rad(speed*0),0,0)
				elseif keys.s then
					gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(math.rad(speed*0),0,0)
				else
					gyro.cframe = workspace.CurrentCamera.CoordinateFrame
				end
			until flying == false
			if gyro then gyro:Destroy() end
			if pos then pos:Destroy() end
			flying=false
			Humanoid.PlatformStand=false
			speed=10
		end
		e1=mouse.KeyDown:connect(function(key)
			if not torso or not torso.Parent then flying=false e1:disconnect() e2:disconnect() return end
			if key=="w" then
				keys.w=true
			elseif key=="s" then
				keys.s=true
			elseif key=="a" then
				keys.a=true
			elseif key=="d" then
				keys.d=true
			elseif key=="x" then
				if flying==true then
					flying=false
				else
					flying=true
					start()
				end
			end
		end)
		e2=mouse.KeyUp:connect(function(key)
			if key=="w" then
				keys.w=false
			elseif key=="s" then
				keys.s=false
			elseif key=="a" then
				keys.a=false
			elseif key=="d" then
				keys.d=false
			end
		end)
		start()
    end)

MainSection:NewButton("Reach", "Allows you to damage players from far away", function(v)
for i,v in pairs(game:GetService'Players'.LocalPlayer.Character:GetChildren())do
	    	if v:isA("Tool") then
	           local a = Instance.new("SelectionBox",v.Handle)
	           a.Adornee = v.Handle
	           v.Handle.Size = Vector3.new(50, 50, 50)
                   v.Handle.Transparency = 30
		   v.Handle.CanCollide = false
	        end
		end
    end)

MainSection:NewButton("God", "Removes damage (dont use if your banned)", function(v)
wait(0) local A_1 = "[Doge Hub] God Enabled." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
loadstring(game:HttpGet("https://pastebin.com/raw/4zHpyqHz", true))()
    end)


MainSection:NewButton("Unban", "Unbans yourself", function(v)
wait(0) local A_1 = "[Doge Hub] Unbanned." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
_G.LoopUnban = false -- true or false
loadstring(game:HttpGet('https://raw.githubusercontent.com/DaHoodScripts/NoUScripts/main/NewUnban'))()
    end)

MainSection:NewButton("Inf Jump", "Allows you to jump many times without stopping", function(v)
wait(0) local A_1 = "[Doge Hub] Inf jump enabled." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 

Player = game:GetService'Players'.LocalPlayer;
	UIS = game:GetService'UserInputService';
	
	_G.JumpHeight = 50;
	
	function Action(Object, Function) if Object ~= nil then Function(Object); end end
	
	UIS.InputBegan:connect(function(UserInput)
	    if UserInput.UserInputType == Enum.UserInputType.Keyboard and UserInput.KeyCode == Enum.KeyCode.Space then
	        Action(Player.Character.Humanoid, function(self)
	            if self:GetState() == Enum.HumanoidStateType.Jumping or self:GetState() == Enum.HumanoidStateType.Freefall then
	                Action(self.Parent.HumanoidRootPart, function(self)
	                    self.Velocity = Vector3.new(0, _G.JumpHeight, 0);
	              		end)
	           		end
	        	end)
	   		 end
		end)

		MainSection:NewButton("ButtonText", "ButtonInfo", function()
			https://raw.githubusercontent.com/Kadennnnnnnn/Autofarm/main/README.md
		end)

Player = game:GetService'Players'.LocalPlayer;
	UIS = game:GetService'UserInputService';
	
	_G.JumpHeight = 50;
	
	function Action(Object, Function) if Object ~= nil then Function(Object); end end
	
	UIS.InputBegan:connect(function(UserInput)
	    if UserInput.UserInputType == Enum.UserInputType.Keyboard and UserInput.KeyCode == Enum.KeyCode.Space then
	        Action(Player.Character.Humanoid, function(self)
	            if self:GetState() == Enum.HumanoidStateType.Jumping or self:GetState() == Enum.HumanoidStateType.Freefall then
	                Action(self.Parent.HumanoidRootPart, function(self)
	                    self.Velocity = Vector3.new(0, _G.JumpHeight, 0);
	              		end)
	           		end
	        	end)
	   		 end
		end)
    end)

	MainSection:NewButton("Crash server", "Crashes the server", function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/racemodex/my-scripts/master/dahoodcrash", true))()
	end)

	MainSection:NewToggle("AutoStomp", "Allows you to AutoStomp", function(v)
    wait(0) local A_1 = "[Doge Hub] AutoStomp on/off" local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
    getgenv().autostomp = v
        while true do
            if not getgenv().autostomp then return end
local script = Instance.new('LocalScript', Auto_Stomp)

	plr = game:GetService('Players').LocalPlayer
	
	repeat wait() until plr.Character:FindFirstChild('Humanoid') or plr.Character:FindFirstChild('xxx')
		hum = plr.Character:FindFirstChild('Humanoid')
			while wait() do
				if plr.Character:FindFirstChild('Humanoid') or plr.Character:FindFirstChild('xxx') then
					wait(.1)
							game.ReplicatedStorage.MainEvent:FireServer("Stomp")
						end
				break
			end
            wait(0)
        end
    end)

	MainSection:NewToggle("AntiBag", "Disables the ability to get bagged", function(v)
wait(0) local A_1 = "[Doge Hub] AntiBag on/off." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
        getgenv().name = v
        while true do
            if not getgenv().name then return end
			local LocalPlayer = game:GetService("Players").LocalPlayer
			local char = LocalPlayer.Character
			char.ChildAdded:Connect(function(sock)
				if sock:IsA("MeshPart") then do
						wait(0)
						sock:Destroy()
					end
				end
			end)
            wait(0)
        end
    end)

	MainSection:NewToggle("AntiFlashbang", "Disables the ability to get flashbanged", function(v)
wait(0) local A_1 = "[Doge Hub] AntiFlash on/off." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
        getgenv().name = v
        while true do
            if not getgenv().name then return end
while true do
		local XD = game:GetService("Players").LocalPlayer.PlayerGui.MainScreenGui

		if XD:FindFirstChild("whiteScreen") then
			XD.whiteScreen:Destroy()
		end
		wait(0.1)
	end
            wait(0)
        end
    end)

local Main = Window:NewTab("Extra")
    local ExtraSection = Main:NewSection("Extra")

	ExtraSection:NewTextBox("Goto", "Teleports to a player", function(txt)
		local TargetPlr = (txt)
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[TargetPlr].Character.HumanoidRootPart.CFrame
	end)

	ExtraSection:NewTextBox("Cash", "Tells you the amt of cash the player has", function(txt)
		local TargetPlr = (txt)
	local A_1 = "[Doge Hub] $" .. game.Players[TargetPlr].DataFolder.Currency.Value .. " " local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2)
	end)

	ExtraSection:NewTextBox("Bag", "Bag's the player", function(txt)
		local TargetPlr = (txt)
	function getRoot(char)
		local rootPart = char:FindFirstChild('HumanoidRootPart') or char:FindFirstChild('Torso') or char:FindFirstChild('UpperTorso')
		return rootPart
	end

	if TargetPlr and game.Players[TargetPlr].Character.BodyEffects['K.O'].Value == false then
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Workspace.Ignored.Shop['[BrownBag] - $25'].Head.CFrame
		wait(0.3)
		fireclickdetector(game.Workspace.Ignored.Shop['[BrownBag] - $25'].ClickDetector)
		game.Players.LocalPlayer.Backpack:WaitForChild("[BrownBag]").Parent = game.Players.LocalPlayer.Character

		local A_1 = "[Doge Hub] Bagging the player" local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2)
		wait(.5)
		repeat
			pcall(function()
				wait()
				getRoot(game.Players[TargetPlr].Character).CFrame = getRoot(game.Players.LocalPlayer.Character).CFrame + Vector3.new(1,3,0)
				game.Players.LocalPlayer.Character["[BrownBag]"]:Activate()
			end)
		until game.Players[TargetPlr].Character:FindFirstChild("Christmas_Sock")
		local A_1 = "[Doge Hub] The player has been bagged" local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2)
	elseif game.Players[TargetPlr].Character.BodyEffects['K.O'].Value == false then
		local A_1 = "[Doge Hub] The player is already bagged" local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2)
	end
	end)

	ExtraSection:NewTextBox("View", "Views a player", function(txt)
		local TargetPlr = (txt)
game.Workspace.Camera.CameraSubject = game.Players[TargetPlr].Character.Humanoid;
	end)

	ExtraSection:NewButton("UnView", "ButtonInfo", function()
		game.Workspace.Camera.CameraSubject = game.Players.LocalPlayer.Character.Humanoid
	end)

ExtraSection:NewButton("Tools while cuffed", "Allows you to use tools while cuffed", function(v)
wait(0) local A_1 = "[Doge Hub] Tools while cuffed." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
LocalPlayer = game.Players.LocalPlayer

LocalPlayer.Character.BodyEffects.Cuff.Value = false
LocalPlayer.Character.BodyEffects.Cuff:Destroy()
    end)

ExtraSection:NewButton("Rejoin", "Rejoins the game", function(v)
TeleportService = game:GetService("TeleportService")
		placeID_1 = 2788229376 
		wait()
		TeleportService:Teleport(placeID_1, plr)
    end)
    
    ExtraSection:NewKeybind("Keybind", "Allows you to add a keybind to toggle gui", Enum.KeyCode.Z, function()
	Library:ToggleUI()
end)


local Player = Window:NewTab("Teleports")
    local TeleportsSection = Player:NewSection("Teleports")

TeleportsSection:NewButton("All guns", "Teleports you to the location", function(v)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-871.855896, -32.7306442, -535.05896, -0.995392859, -4.0865018e-08, 0.0958791748, -4.15632648e-08, 1, -5.28550803e-09, -0.0958791748, -9.24621002e-09, -0.995392859)
    end)

TeleportsSection:NewButton("Gun shop 1", "Teleports you to the location", function(v)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-564.286072, 7.99984741, -737.080627, -0.062280681, 0, 0.998058677, 0, 1, 0, -0.998058677, 0, -0.062280681)
    end)

TeleportsSection:NewButton("Gun shop 2", "Teleports you to the location", function(v)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(481.144287, 48.0050011, -606.490051, 0.997044683, 4.43454518e-08, -0.0768238455, -4.82029563e-08, 1, -4.83580465e-08, 0.0768238455, 5.1918267e-08, 0.997044683)
    end)

TeleportsSection:NewButton("Bank", "Teleports you to the location", function(v)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-407.866272, 21.75, -281.132416, 0.0552855767, 5.23181782e-08, 0.998470604, 6.93292961e-08, 1, -5.62370985e-08, -0.998470604, 7.23323623e-08, 0.0552855767)
    end)

TeleportsSection:NewButton("Casino", "Teleports you to the location", function(v)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-827.856201, 21.2549973, -180.739929, -0.998989165, 1.3394204e-08, -0.0449521728, 1.2559739e-08, 1, 1.88458227e-08, 0.0449521728, 1.82621847e-08, -0.998989165)
    end)

TeleportsSection:NewButton("Admin base", "Teleports you to the location", function(v)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-797.8078, -39.6492004, -899.534851, -0.999981701, -4.12056389e-09, 0.00603817962, -4.31152092e-09, 1, -3.16118118e-08, -0.00603817962, -3.1637267e-08, -0.999981701)
    end)


    -- Credits
    local Player = Window:NewTab("Credits")
    local CreditsSection = Player:NewSection("CrispyExploitz")
    local CreditsSection = Player:NewSection("ChoppaGoBrrrr#3017")
    local CreditsSection = Player:NewSection("https://discord.gg/FkadkNN5")
end
