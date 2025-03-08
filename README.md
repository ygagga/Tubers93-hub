local Vape = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/UI-Libs/main/Vape.txt"))()
local Window = Vape:Window(
    "Troll Hub", -- Título
    Color3.fromRGB(44, 120, 224), -- Cor
    Enum.KeyCode.RightControl -- Tecla para abrir/fechar
)

local Tab = Window:Tab("Controle de Jogadores")

-- Seleção de jogador
Tab:Dropdown(
    "Selecionar Jogador", 
    {"Jogador1", "Jogador2", "Jogador3"}, 
    function(Value)
        print("Jogador selecionado:", Value)
        selectedPlayer = Value
    end
)

-- ESP Toggle
Tab:Toggle(
    "Ativar ESP", 
    false, 
    function(Value)
        if Value then
            print("ESP ativado")
        else
            print("ESP desativado")
        end
    end
)

-- Teleportar para o jogador selecionado
Tab:Button("Teleportar para o Jogador", function()
    if selectedPlayer then
        print("Teleportando para", selectedPlayer)
        -- Código para teleportar para o jogador
    else
        print("Nenhum jogador selecionado!")
    end
end)

-- Espectar jogador
Tab:Button("Espectar Jogador", function()
    if selectedPlayer then
        print("Espectando", selectedPlayer)
        -- Código para espectar o jogador
    else
        print("Nenhum jogador selecionado!")
    end
end)

-- Despectar jogador
Tab:Button("Despectar", function()
    print("Despectando...")
    -- Código para despectar
end)

-- Teleportar todos para o jogador
Tab:Button("Teleportar Todos para Você", function()
    print("Teleportando todos os jogadores para você...")
    -- Código para teleportar todos os jogadores
end)

local ScriptsTab = Window:Tab("Scripts Universais")

-- Carregar o RAEL Hub
ScriptsTab:Button("Carregar RAEL Hub", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Laelmano24/Rael-Hub/main/main.txt"))()
end)

-- Carregar o Fly Gui V3
ScriptsTab:Button("Carregar Fly Gui V3", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/XNEOFF/FlyGuiV3/main/FlyGuiV3.txt"))()
end)

-- Carregar o Sander X
ScriptsTab:Button("Carregar Sander X", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/sXPiterXs1111/Sanderxv3.30/main/sanderx3.30'))()
end)

-- Notificação
Vape:Notification(
    "Troll Hub", 
    "Interface Carregada com Sucesso", 
    "Aproveite as funcionalidades!"
)
