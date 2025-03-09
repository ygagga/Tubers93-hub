-- Carregar a biblioteca Rayfield
local Rayfield = loadstring(game:HttpGet("https://raw.githubusercontent.com/CCB-RBLX/Rayfield/main/source.lua"))()

-- Criando a Janela da Interface
local Window = Rayfield:CreateWindow({
    Name = "Brookhaven RP 🏡 (Troll Hub 🤡)",
    LoadingTitle = "Carregando...",
    LoadingSubtitle = "Por favor, aguarde...",
    ConfigurationSaving = {
        Enabled = true,
        FolderName = "Rayfield",
        FileName = "TrollHub"
    },
    Discord = {
        Enabled = true,
        Invite = "discord.gg/example",
        RememberJoins = true
    },
    KeySystem = true,
    KeySettings = {
        Key = "TROLL",
        KeyEnabled = true,
        KeyCooldown = 5,
        KeyCheckInterval = 1
    }
})

-- Criando a Aba Troll
local TrollTab = Window:CreateTab("🤡 Troll", 4483362458)

TrollTab:CreateSection("Controle de Jogadores")

local selectedPlayer = ""

-- Campo de entrada para o nome do jogador
TrollTab:CreateInput({
    Name = "Nome do Jogador",
    PlaceholderText = "Digite o nome do jogador",
    RemoveTextAfterFocusLost = false,
    Callback = function(value)
        selectedPlayer = value
    end
})

-- Função para trazer todas as partes para o jogador selecionado
local function bringAllPartsToPlayer()
    local targetPlayer = game.Players:FindFirstChild(selectedPlayer)

    if not targetPlayer or not targetPlayer.Character then
        warn("Jogador inválido!")
        return
    end

    local targetRoot = targetPlayer.Character:FindFirstChild("HumanoidRootPart")
    if not targetRoot then return end

    -- Percorrer todas as partes no jogo
    for _, part in pairs(workspace:GetDescendants()) do
        if part:IsA("BasePart") and not part:IsDescendantOf(targetPlayer.Character) then
            part.CFrame = targetRoot.CFrame + Vector3.new(math.random(-5, 5), 3, math.random(-5, 5))
        end
    end
end

-- Botão para trazer todas as partes para o jogador selecionado
TrollTab:CreateButton({
    Name = "Trazer Todas as Partes 🔄",
    Description = "Traz todas as partes possíveis do mapa para o jogador selecionado.",
    Callback = function()
        bringAllPartsToPlayer()
    end
})
