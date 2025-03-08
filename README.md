-- Carregar a Asrua UI
local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/ahsrua/AsruaUI/main/sursa.lua"))():MakePrototypeLibrary("Troll Hub")

-- Criar a aba principal
local MainTab = Lib:MakeTab("Troll Hub", true)

-- Obter lista de jogadores
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local selectedPlayer = nil

-- Atualizar a lista de jogadores
function GetPlayerList()
    local playerList = {}
    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer then
            table.insert(playerList, player.Name)
        end
    end
    return playerList
end

-- Dropdown para selecionar jogadores
MainTab:Dropdown("Selecionar Jogador", GetPlayerList(), function(Value)
    selectedPlayer = Players:FindFirstChild(Value)
    print("Selecionado:", Value)
end)

-- ESP Toggle
MainTab:Toggle("Ativar ESP", function(State)
    if State then
        for _, player in pairs(Players:GetPlayers()) do
            if player.Character and not player.Character:FindFirstChild("ESP") then
                local highlight = Instance.new("Highlight")
                highlight.Name = "ESP"
                highlight.Adornee = player.Character
                highlight.Parent = player.Character
            end
        end
        print("ESP ativado")
    else
        for _, player in pairs(Players:GetPlayers()) do
            if player.Character and player.Character:FindFirstChild("ESP") then
                player.Character:FindFirstChild("ESP"):Destroy()
            end
        end
        print("ESP desativado")
    end
end)

-- Função de teleportar até o jogador
MainTab:Button("Teleportar para o Jogador", function()
    if selectedPlayer and selectedPlayer.Character and LocalPlayer.Character then
        LocalPlayer.Character.HumanoidRootPart.CFrame = selectedPlayer.Character.HumanoidRootPart.CFrame
        print("Teleportado para:", selectedPlayer.Name)
    else
        print("Nenhum jogador selecionado ou erro no teleport!")
    end
end)

-- Espectar jogador
MainTab:Button("Espectar Jogador", function()
    if selectedPlayer and selectedPlayer.Character then
        LocalPlayer.CameraSubject = selectedPlayer.Character:FindFirstChildWhichIsA("Humanoid")
        print("Espectando:", selectedPlayer.Name)
    else
        print("Erro ao espectar!")
    end
end)

-- Despectar jogador
MainTab:Button("Despectar", function()
    LocalPlayer.CameraSubject = LocalPlayer.Character:FindFirstChildWhichIsA("Humanoid")
    print("Despectando...")
end)

-- Teleportar todos para você
MainTab:Button("Teleportar Todos para Você", function()
    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and player.Character then
            player.Character.HumanoidRootPart.CFrame = LocalPlayer.Character.HumanoidRootPart.CFrame
        end
    end
    print("Todos teleportados para você!")
end)

-- Criar uma nova aba para Scripts Universais
local ScriptsTab = Lib:MakeTab("Scripts Universais")

-- Funções do Troll Hub
ScriptsTab:Button("Lagar o servidor", function()
    for i = 1, 100 do
        game:GetService("ReplicatedStorage").Events.PlaceStructure:FireServer()
    end
    print("Largando o servidor...")
end)

ScriptsTab:Button("Aumentar velocidade", function()
    LocalPlayer.Character.Humanoid.WalkSpeed = 100
    print("Velocidade aumentada!")
end)

ScriptsTab:Button("Tocar som específico", function()
    local sound = Instance.new("Sound", LocalPlayer.Character)
    sound.SoundId = "rbxassetid://1234567890" -- Troque pelo ID do som desejado
    sound:Play()
    print("Tocando som...")
end)

ScriptsTab:Button("Matar jogador (Carro/Sofá)", function()
    if selected
    
