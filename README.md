local Material = loadstring(game:HttpGet("https://raw.githubusercontent.com/Kinlei/MaterialLua/master/Module.lua"))()

local UI =
    Material.Load(
    {
        Title = "BOOGA BOOGA HYBIRD HUB",
        Style = 3,
        SizeX = 400,
        SizeY = 250,
        Theme = "Dark"
    }
)


local Page = UI.New({
    Title = "booga booga hybird HUB"
})



Page.Button({
    Text = "esp",
    Callback = function()
        function CreateSG(name,parent,face)
    local SurfaceGui = Instance.new("SurfaceGui",parent)
    SurfaceGui.Parent = parent
    SurfaceGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    SurfaceGui.Face = Enum.NormalId[face]
	SurfaceGui.LightInfluence = 0
	SurfaceGui.ResetOnSpawn = false
    SurfaceGui.Name = name
    SurfaceGui.AlwaysOnTop = true
    local Frame = Instance.new("Frame",SurfaceGui)
	Frame.BackgroundColor3 = Color3.fromRGB(85, 170, 255)
	Frame.Size = UDim2.new(1,0,1,0)
end

while wait(1) do
for i,v in pairs (game:GetService("Players"):GetPlayers()) do
    if v ~= game:GetService("Players").LocalPlayer and v.Character ~= nil and v.Character:FindFirstChild("Head") and v.Character.Head:FindFirstChild("cham") == nil then
        for i,v in pairs (v.Character:GetChildren()) do
        if v:IsA("MeshPart") or v.Name == "Head" then
        CreateSG("cham",v,"Back")
        CreateSG("cham",v,"Front")
        CreateSG("cham",v,"Left")
        CreateSG("cham",v,"Right")
        CreateSG("cham",v,"Right")
        --CreateSG("cham",v,"Top")
        CreateSG("cham",v,"Bottom")
        end
        end
    end
end
end
        print("Clicked!")
    end
})



Page.Button({
    Text = "Remove effects/fog",
    Callback = function()
        while true do
wait()
game.Lighting.FogEnd = 1000000
wait()
end
        print("Clicked!")    
    end
})


Page.Button({
    Text = "InfiniteJump",
    Callback = function()
        InfiniteJumpEnabled = true
game:GetService("UserInputService").JumpRequest:connect(function()
    if InfiniteJumpEnabled then
        game:GetService"Players".LocalPlayer.Character:FindFirstChildOfClass'Humanoid':ChangeState("Jumping")
    end
end)
        print("Clicked!")
    end
})


Page.Button(
    {
        Text = "tp to void",
        Callback = function()
            game:GetService("TeleportService"):Teleport("5900986119")
            print("Clicked!")
        end
    }
)

Page.Button(
    {
        Text = "Bloodfruit auto farm",
        Callback = function()
            local placekey = "p"
            local plantkey = "["
            local collectkey = "]"
            local amountofpots = 40

            ----------------no touchy below plz

            local Player = game:GetService("Players").LocalPlayer
            local Mouse = Player:GetMouse()

            _G.plant = function()
                for _, v in pairs(workspace.Deployables:GetChildren()) do
                    if
                        v.Name == "Plant Box" and
                            (Player.Character.Head.Position - v.PrimaryPart.Position).magnitude < 500
                     then
                        game.ReplicatedStorage.Events.InteractStructure:FireServer(v, "Bloodfruit")
                    end
                end
            end

            _G.collect = function()
                for _, v in pairs(workspace:GetChildren()) do
                    if
                        v.Name == "Bloodfruit Bush" and
                            (Player.Character.Head.Position - v.PrimaryPart.Position).magnitude < 50
                     then
                        game.ReplicatedStorage.Events.Pickup:FireServer(v)
                    end
                end
            end

            Mouse.KeyUp:connect(
                function(k)
                    if k == placekey then
                        for i = 1, amountofpots do
                            game.ReplicatedStorage.Events.PlaceStructure:FireServer("Plant Box", Mouse.Hit, 0)
                        end
                    elseif k == plantkey then
                        _G.plant()
                    elseif k == collectkey then
                        _G.collect()
                    end
                end
            )
            print("Clicked!")
        end
    }
)

Page.Button(
    {
        Text = "auto farm jelly",
        Callback = function()
            UI.Banner({
    Text = "auto farm jelly p to use"
})
            local placekey = "p"
            local plantkey = "["
            local collectkey = "]"
            local amountofpots = 40 ----------------oh yeah i forgot to mention this but you actually need to have the leaves and sticks required to make x number of plant pots

            ----------------no touchy below plz

            local Player = game:GetService("Players").LocalPlayer
            local Mouse = Player:GetMouse()

            _G.plant = function()
                for _, v in pairs(workspace.Deployables:GetChildren()) do
                    if
                        v.Name == "Plant Box" and
                            (Player.Character.Head.Position - v.PrimaryPart.Position).magnitude < 500
                     then
                        game.ReplicatedStorage.Events.InteractStructure:FireServer(v, "Jelly")
                    end
                end
            end

            _G.collect = function()
                for _, v in pairs(workspace:GetChildren()) do
                    if
                        v.Name == "Jelly Crop" and
                            (Player.Character.Head.Position - v.PrimaryPart.Position).magnitude < 50
                     then
                        game.ReplicatedStorage.Events.Pickup:FireServer(v)
                    end
                end
            end

            Mouse.KeyUp:connect(
                function(k)
                    if k == placekey then
                        for i = 1, amountofpots do
                            game.ReplicatedStorage.Events.PlaceStructure:FireServer("Plant Box", Mouse.Hit, 0)
                        end
                    elseif k == plantkey then
                        _G.plant()
                    elseif k == collectkey then
                        _G.collect()
                    end
                end
            )
            print("Clicked!")
        end
    }
)

Page.Button(
    {
        Text = "TP back",
        Callback = function()
            game:GetService("TeleportService"):Teleport("5901346231")
            print("Clicked!")
        end
    }
)



Page.Button(
    {
        Text = "ctrl to tp",
        Callback = function()
            local plr = game:GetService("Players").LocalPlayer
            local hum = plr.Character.HumanoidRootPart
            local mouse = plr:GetMouse()
            --+--
            local speed = 0.900
            --+--
            local mouseconnection
            game:GetService("UserInputService").InputBegan:Connect(
                function(i, g)
                    if not g and i.KeyCode == Enum.KeyCode.LeftControl then --- the hot key is "LeftControl" You can change it to anything like e or q just aslong as u hold the key you chose it should work
                        mouseconnection =
                            mouse.Button1Down:Connect(
                            function()
                                game:GetService("TweenService"):Create(
                                    hum,
                                    TweenInfo.new(speed),
                                    {CFrame = CFrame.new(mouse.Hit.p + Vector3.new(0, 3, 0))}
                                ):Play()
                            end
                        )
                    end
                end
            )
            game:GetService("UserInputService").InputEnded:Connect(
                function(i, g)
                    if i.KeyCode == Enum.KeyCode.LeftControl and mouseconnection then
                        mouseconnection:Disconnect()
                    end
                end
            )
            print("Clicked!")
        end
    }
)


local Page = UI.New({
    Title = "Misc"
})



Page.Button({
    Text = "float",
Callback = function()
    UI.Banner({
    Text = "e to float"
})
        
local s = loadstring(game:HttpGet(("https://raw.githubusercontent.com/RobloxScripts52/noclip/main/noclip.lua"), true))()
print(s)
        print("Clicked!")    
    end
})



Page.Button({
    Text = "Kick self",
    Callback = function()
    _G.message = "kicked form game"
local shutdown = game.Players.LocalPlayer
shutdown:Kick(_G.message)
        print("Clicked!")    
    end
})

Page.Button({
    Text = "auto pickup",
    Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Freshy-github/Freshy-Hub-Function/main/b", true))()
        print("Clicked!")    
    end
})








