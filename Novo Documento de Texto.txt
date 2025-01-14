--abaixo estara a lib da nossa ui

local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/7yhx/kwargs_Ui_Library/main/source.lua"))()

local UI = Lib:Create{
   Theme = "Dark", -- or any other theme
   Size = UDim2.new(0, 555, 0, 400) -- default
}

local Main = UI:Tab{
   Name = "inicio"
}

local Divider = Main:Divider{
   Name = "inicio shit"
}

local QuitDivider = Main:Divider{
   Name = "sair"
}

-- Configurações do script
local showFOV = true
local showArrows = true
local showBoxes = true
local toggleKey = Enum.KeyCode.F

-- Função para alternar o estado do script
local function toggleScript()
    showFOV = not showFOV
    showArrows = not showArrows
    showBoxes = not showBoxes
end

-- Conectar a tecla de atalho
game:GetService("UserInputService").InputBegan:Connect(function(input)
    if input.KeyCode == toggleKey then
        toggleScript()
    end
end)

-- Função para marcar jogadores
local function markPlayers()
    for _, player in pairs(game.Players:GetPlayers()) do
        if player ~= game.Players.LocalPlayer then
            local character = player.Character
            if character and character:FindFirstChild("Head") then
                if showFOV then
                    -- Código para desenhar FOV ao redor dos inimigos
                end
                if showArrows then
                    -- Código para desenhar setas indicando a direção dos inimigos
                end
                if showBoxes and player.Team ~= game.Players.LocalPlayer.Team then
                    -- Código para desenhar caixas vermelhas ao redor dos inimigos
                end
            end
        end
    end
end

-- Loop principal para atualizar as marcações
game:GetService("RunService").RenderStepped:Connect(markPlayers)
