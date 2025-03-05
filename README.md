local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
    Title = "Brookhaven Rp🏡",
    SubTitle = "by (tubers hub)",
    TabWidth = 160,
    Size = UDim2.fromOffset(480, 310),
    Acrylic = true,
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl
})

-- Fonction permettant de changer d'avatar.
-- Si l'argument "id" est une table, on l'utilise tel quel ; sinon, on crée la table par défaut.
local function fireAvatarChange(id, notificationTitle)
    local argsTable
    if type(id) == "table" then
        argsTable = id
    else
        argsTable = {1, 1, 1, 1, 1, id}
    end

    local args = {
        [1] = "CharacterChange",
        [2] = argsTable,
        [3] = "z4troxhub"
    }

    local replicatedStorage = game:GetService("ReplicatedStorage")
    local starterGui = game:GetService("StarterGui")

    if replicatedStorage and starterGui then
        local remote = replicatedStorage.RE:FindFirstChild("1Avata1rOrigina1l")
        if remote then
            remote:FireServer(unpack(args))
            starterGui:SetCore("SendNotification", {
                Title = notificationTitle,
                Text = "Wait Please 1-10 Seconds",
                Duration = 5
            })
        end
    end
end

-- Création des tabs
local Tabs = {
    Credits = Window:AddTab({ Title = "z4trox Hub Tab", Icon = "scroll" }),
    Avatar = Window:AddTab({ Title = "Avatar Tab", Icon = "shirt" }),
    Bundles = Window:AddTab({ Title = "Bundle Tab", Icon = "users" }),
    Music = Window:AddTab({ Title = "Music Tab", Icon = "music" })
}

-----------------------------------------------------------
-- Section Avatar
-----------------------------------------------------------
Tabs.Avatar:AddSection("Head ID (❓)/Yellow Pastel (🟡)")

Tabs.Avatar:AddInput("Head ID (❓)", {
    Title = "Head ID (❓)",
    Default = "",
    Placeholder = "ID",
    Numeric = true,
    Finished = true,
    Callback = function(s)
        fireAvatarChange(tonumber(s), "Loading")
        wait(1)
        game:GetService("StarterGui"):SetCore("SendNotification", {
            Title = "Done",
            Text = "Successfully ✅",
            Duration = 3
        })
    end
})

Tabs.Avatar:AddButton({
    Title = "Pastel Yellow (🟡)",
    Description = "",
    Callback = function()
        fireAvatarChange("Pastel yellow", "Pastel Yellow Applied")
    end
})

Tabs.Avatar:AddSection("Character Head (👤)")

Tabs.Avatar:AddButton({
    Title = "Headless Horseman (👤)",
    Description = "Working 🔨",
    Callback = function()
        fireAvatarChange(134082579, "Headless Horseman")
    end
})

Tabs.Avatar:AddButton({
    Title = "Blaze Burner (👤)",
    Description = "Working 🔨",
    Callback = function()
        fireAvatarChange(3210773801, "Blaze Burner")
    end
})

Tabs.Avatar:AddButton({
    Title = "Korblox DeathSpeaker (👤)",
    Description = "Working 🔨",
    Callback = function()
        fireAvatarChange(16580493236, "Korblox DeathSpeaker")
    end
})

Tabs.Avatar:AddSection("Classic Head (👥)")

Tabs.Avatar:AddButton({
    Title = "Classic Head (👥)",
    Description = "Working 🔨",
    Callback = function()
        fireAvatarChange(746767604, "Classic Head")
    end
})

Tabs.Avatar:AddButton({
    Title = "Strong Jaw (👥)",
    Description = "Working 🔨",
    Callback = function()
        fireAvatarChange(616399508, "Strong Jaw")
    end
})

Tabs.Avatar:AddButton({
    Title = "Narrow Head (👥)",
    Description = "Working 🔨",
    Callback = function()
        fireAvatarChange(746774687, "Narrow Head")
    end
})

Tabs.Avatar:AddButton({
    Title = "Chiseled Head (👥)",
    Description = "Working 🔨",
    Callback = function()
        fireAvatarChange(616387160, "Chiseled Head")
    end
})

Tabs.Avatar:AddButton({
    Title = "Paragon Head (👥)",
    Description = "Working 🔨",
    Callback = function()
        fireAvatarChange(616398268, "Paragon Head")
    end
})

-----------------------------------------------------------
-- Section Bundles (avatars spécifiques)
-----------------------------------------------------------
Tabs.Bundles:AddButton({
    Title = "Inf15 Thin",
    Description = "(Boy) U Need Body Avatar",
    Callback = function()
        fireAvatarChange({
            17873152058, 17873151683, 17873151726, 17873151827, 17873152017, 1
        }, "Inf15 Thin")
    end
})

Tabs.Bundles:AddButton({
    Title = "Blush Fashion Doll (Black Torso)",
    Description = "(Girl) Woman Arm/No Leg",
    Callback = function()
        fireAvatarChange({
            96491916349570, 86499698, 86499716, 0, 0, 0
        }, "Blush Fashion Doll")
    end
})

Tabs.Bundles:AddButton({
    Title = "Mini Plushie",
    Description = "(Boy, Girl) U Need Small Body Ava",
    Callback = function()
        fireAvatarChange({
            18865136555, 14579959062, 14579959191, 14579959249, 14579963667, 1
        }, "Mini Plushie")
    end
})

-----------------------------------------------------------
-- Section Music
-----------------------------------------------------------
Tabs.Music:AddSection("Music Section")

Tabs.Music:AddInput("Enter Music ID", {
    Title = "Enter Music ID",
    Default = "",
    Placeholder = "Enter ID here",
    Finished = true,
    Callback = function(Value)
        local args = {
            [1] = "PickingScooterMusicText",
            [2] = Value
        }
        local replicatedStorage = game:GetService("ReplicatedStorage")
        local remote = replicatedStorage.RE:FindFirstChild("1NoMoto1rVehicle1s")
        if remote then
            remote:FireServer(unpack(args))
        end
    end
})

-----------------------------------------------------------
-- Section Credits
-----------------------------------------------------------
Tabs.Credits:AddSection("Update Logs📜/Credit 💳")
Tabs.Credits:AddParagraph({
    Title = "Update Logs 📜",
    Content = "Added Bundles\nNew UI Library"
})
Tabs.Credits:AddParagraph({
    Title = "Credit 💳",
    Content = "Discord💬 user: snobodj"
})
