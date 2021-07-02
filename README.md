placeid = 2788229376
if game.PlaceId == placeid then
    local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
    local Window = Library.CreateLib("Azure")

    -- Main
    local Main = Window:NewTab("Scripts")
    local MainSection = Main:NewSection("Scripts")

    MainSection:NewButton("Fly", "Allows you to fly", function(v)
wait(0) local A_1 = "[Azure] Fly enabled." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
	local plr = game.Players.LocalPlayer
	local mouse = plr:GetMouse()

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
	local speed=50
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
			localplayer.Character.Humanoid.PlatformStand=true
			local new=gyro.cframe - gyro.cframe.p + pos.position
			if not keys.w and not keys.s and not keys.a and not keys.d then
				speed=50
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
				speed=50
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
		localplayer.Character.Humanoid.PlatformStand=false
		speed=50
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
wait(0) local A_1 = "[Azure] Reach enabled." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
for i,v in pairs(game:GetService'Players'.LocalPlayer.Character:GetChildren())do
	    	if v:isA("Tool") then
	           local a = Instance.new("SelectionBox",v.Handle)
	           a.Adornee = v.Handle
	           v.Handle.Size = Vector3.new(50, 50, 50)
                   v.Handle.Transparency = 30
	        end
		end
    end)

MainSection:NewButton("GodBullet", "Removes bullet damage (dont use if your banned)", function(v)
wait(0) local A_1 = "[Azure] GodBullet Enabled." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
local ps = game:GetService("Players")
	local lp = ps.LocalPlayer
	local char = lp.Character

	char.BodyEffects.Armor:Destroy()
	char.BodyEffects.Defense:Destroy()

	local Clone1 = Instance.new("IntValue")
	Clone1.Name = "Armor"
	Clone1.Parent = char.BodyEffects

	local Clone2 = Instance.new("NumberValue")
	Clone2.Name = "Defense"
	Clone2.Parent = char.BodyEffects
    end)


MainSection:NewButton("Unban", "Unbans yourself", function(v)
wait(0) local A_1 = "[Azure] Unbanned." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
_G.LoopUnban = false -- true or false
loadstring(game:HttpGet('https://raw.githubusercontent.com/DaHoodScripts/NoUScripts/main/NewUnban'))()
    end)


MainSection:NewButton("Inf Jump", "Allows you to jump many times without stopping", function(v)
wait(0) local A_1 = "[Azure] Inf jump enabled." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 

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

    local Player = Window:NewTab("Toggles")
    local TogglesSection = Player:NewSection("Toggles")

TogglesSection:NewToggle("AutoStomp", "Allows you to AutoStomp", function(v)
    wait(0) local A_1 = "[Azure] Autostomp on/off" local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
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

local Main = Window:NewTab("Extra")
    local ExtraSection = Main:NewSection("Extra")

ExtraSection:NewButton("Tools while cuffed", "Allows you to use tools while cuffed", function(v)
wait(0) local A_1 = "[Azure] Tools while cuffed." local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
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


    -- Credits
    local Player = Window:NewTab("Credits")
    local CreditsSection = Player:NewSection("CrispyExploitz")
    local CreditsSection = Player:NewSection("Crispy#3017")
    local CreditsSection = Player:NewSection("https://discord.gg/FkadkNN5")
end
