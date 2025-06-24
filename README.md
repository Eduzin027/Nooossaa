--[[
    EduardoHub - Universal Script (Base GUI)
    Suporte: Blox Fruits, Pet Simulator X, Brookhaven, Blade Ball, etc.
    Status: Exemplo Educacional (incompleto - requer complementos por jogo)
--]]

-- Carregar biblioteca UI (por exemplo, Orion Library)
loadstring(game:HttpGet("https://raw.githubusercontent.com/shlexware/Orion/main/source"))()

local Window = OrionLib:MakeWindow({Name = "EduardoHub", HidePremium = false, SaveConfig = true, ConfigFolder = "EduardoHubConfig"})

-- Detectar jogo atual
local gameId = game.PlaceId

-- Funções Comuns
function antiAFK()
    local VirtualUser = game:service'VirtualUser'
    game:service'Players'.LocalPlayer.Idled:connect(function()
        VirtualUser:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
        wait(1)
        VirtualUser:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
    end)
end

antiAFK()

-- Blox Fruits Setup
if gameId == 2753915549 or gameId == 4442272183 or gameId == 7449423635 then
    local Tab = Window:MakeTab({Name = "Blox Fruits", Icon = "rbxassetid://4483345998", PremiumOnly = false})

    Tab:AddButton({
        Name = "Auto Farm Level",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/eduardohub/scripts/main/bloxfruits_autofarm.lua"))()
        end
    })

    Tab:AddButton({
        Name = "Auto Stats",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/eduardohub/scripts/main/bloxfruits_autostats.lua"))()
        end
    })

    Tab:AddButton({
        Name = "Teleport Islands",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/eduardohub/scripts/main/bloxfruits_tp.lua"))()
        end
    })
end

-- Pet Simulator X
if gameId == 6284583030 then
    local Tab = Window:MakeTab({Name = "Pet Simulator X", Icon = "rbxassetid://4483345998", PremiumOnly = false})

    Tab:AddButton({
        Name = "Auto Farm Coins",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/eduardohub/scripts/main/petsim_autofarm.lua"))()
        end
    })
end

-- Blade Ball
if gameId == 13772394625 then
    local Tab = Window:MakeTab({Name = "Blade Ball", Icon = "rbxassetid://4483345998", PremiumOnly = false})

    Tab:AddButton({
        Name = "Auto Parry / Block",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/eduardohub/scripts/main/bladeball_autoparry.lua"))()
        end
    })
end

-- Brookhaven
if gameId == 4924922222 then
    local Tab = Window:MakeTab({Name = "Brookhaven", Icon = "rbxassetid://4483345998", PremiumOnly = false})

    Tab:AddButton({
        Name = "God Mode + Itens Grátis",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/eduardohub/scripts/main/brookhaven.lua"))()
        end
    })
end

-- Créditos
local Tab = Window:MakeTab({Name = "Sobre", Icon = "rbxassetid://6034996695", PremiumOnly = false})
Tab:AddParagraph("EduardoHub Script", "Hub Multi-Jogos personalizado por Eduardo.")
