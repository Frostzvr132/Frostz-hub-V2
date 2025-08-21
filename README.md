-- LocalScript (StarterGui)

local Player = game.Players.LocalPlayer
local PlayerGui = Player:WaitForChild("PlayerGui")
local UserInputService = game:GetService("UserInputService")

-- Lista de Keys válidas
local Keys = {
    "Frostz Hub",
    "Viny",
    "Frostz Fire"
}

-- Config
local SaveFile = "FrostzHubKey.txt" -- nome do arquivo para salvar a key
local SavedKey = nil

-- Tenta carregar a key salva
if isfile and readfile and isfile(SaveFile) then
    SavedKey = readfile(SaveFile)
end

-- Criando a ScreenGui
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "FrostzHub"
ScreenGui.Parent = PlayerGui
ScreenGui.ResetOnSpawn = false

-- Frame da Tela de Key
local KeyFrame = Instance.new("Frame")
KeyFrame.Size = UDim2.new(0, 300, 0, 150)
KeyFrame.Position = UDim2.new(0.5, -150, 0.5, -75)
KeyFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
KeyFrame.Active = true
KeyFrame.Draggable = true
KeyFrame.Parent = ScreenGui

local UICornerKF = Instance.new("UICorner")
UICornerKF.CornerRadius = UDim.new(0, 12)
UICornerKF.Parent = KeyFrame

-- Título
local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, 0, 0, 40)
Title.BackgroundTransparency = 1
Title.Text = "🔑 Frostz Hub - Key System"
Title.Font = Enum.Font.GothamBold
Title.TextSize = 16
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Parent = KeyFrame

-- Caixa de Texto para a Key
local KeyBox = Instance.new("TextBox")
KeyBox.Size = UDim2.new(0.8, 0, 0, 30)
KeyBox.Position = UDim2.new(0.1, 0, 0.4, 0)
KeyBox.PlaceholderText = "Digite sua Key..."
KeyBox.Text = ""
KeyBox.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
KeyBox.TextColor3 = Color3.fromRGB(255, 255, 255)
KeyBox.Font = Enum.Font.Gotham
KeyBox.TextSize = 14
KeyBox.Parent = KeyFrame

local cornerKB = Instance.new("UICorner")
cornerKB.CornerRadius = UDim.new(0, 8)
cornerKB.Parent = KeyBox

-- Botão de Verificar
local CheckButton = Instance.new("TextButton")
CheckButton.Size = UDim2.new(0.5, 0, 0, 30)
CheckButton.Position = UDim2.new(0.25, 0, 0.7, 0)
CheckButton.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
CheckButton.Text = "Verificar Key"
CheckButton.TextColor3 = Color3.fromRGB(255, 255, 255)
CheckButton.Font = Enum.Font.Gotham
CheckButton.TextSize = 14
CheckButton.Parent = KeyFrame

local cornerBTN = Instance.new("UICorner")
cornerBTN.CornerRadius = UDim.new(0, 8)
cornerBTN.Parent = CheckButton

-- Mensagem de Status
local StatusLabel = Instance.new("TextLabel")
StatusLabel.Size = UDim2.new(1, 0, 0, 20)
StatusLabel.Position = UDim2.new(0, 0, 1, -20)
StatusLabel.BackgroundTransparency = 1
StatusLabel.Text = ""
StatusLabel.Font = Enum.Font.Gotham
StatusLabel.TextSize = 12
StatusLabel.TextColor3 = Color3.fromRGB(255, 100, 100)
StatusLabel.Parent = KeyFrame

-- GUI Principal (fica oculta até acertar a Key)
local MainFrame = Instance.new("Frame")
MainFrame.Size = UDim2.new(0, 400, 0, 250)
MainFrame.Position = UDim2.new(0.5, -200, 0.5, -125)
MainFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.Visible = false
MainFrame.Parent = ScreenGui

local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 12)
UICorner.Parent = MainFrame

-- Título da Hub
local HubTitle = Instance.new("TextLabel")
HubTitle.Size = UDim2.new(1, 0, 0, 40)
HubTitle.BackgroundTransparency = 1
HubTitle.Text = "⚡ Frostz Hub - Beta V2"
HubTitle.Font = Enum.Font.GothamBold
HubTitle.TextSize = 18
HubTitle.TextColor3 = Color3.fromRGB(255, 255, 255)
HubTitle.Parent = MainFrame

-- Função Criar Botão
local function CriarBotao(nome, ordem, callback)
    local Botao = Instance.new("TextButton")
    Botao.Size = UDim2.new(0.9, 0, 0, 30)
    Botao.Position = UDim2.new(0.05, 0, 0, 50 + (ordem * 35))
    Botao.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    Botao.TextColor3 = Color3.fromRGB(255, 255, 255)
    Botao.Text = nome
    Botao.Font = Enum.Font.Gotham
    Botao.TextSize = 14
    Botao.Parent = MainFrame

    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 8)
    corner.Parent = Botao

    Botao.MouseButton1Click:Connect(callback)
end


-- Criando Botões do Hub
CriarBotao("Miranda Tween", 1, function()
    loadstring(game:HttpGet("https://pastefy.app/mTbfVy0H/raw", true))()
end)
CriarBotao("Miranda Hop", 2, function()
    loadstring(game:HttpGet("https://gist.githubusercontent.com/Kauaicaro10-12/a3a950be0b587bc41dd927713633005e/raw/79e5d795393de33181b889fe0d57fb56fd741df8/MIRANDAHOP23do07.lua"))()
end)
CriarBotao("Lennon Tween", 3, function()
    loadstring(game:HttpGet("https://pastefy.app/1FPEhJmq/raw"))()
end)

-- Créditos
local Criador = Instance.new("TextLabel")
Criador.Size = UDim2.new(1, -20, 0, 30)
Criador.Position = UDim2.new(0, 10, 1, -40)
Criador.BackgroundTransparency = 1
Criador.Text = "✨ Frostz Hub by Viny"
Criador.Font = Enum.Font.Gotham
Criador.TextSize = 14
Criador.TextColor3 = Color3.fromRGB(200, 200, 200)
Criador.Parent = MainFrame

-- Botão Flutuante (toggle para mobile)
local ToggleButton = Instance.new("TextButton")
ToggleButton.Size = UDim2.new(0, 50, 0, 50)
ToggleButton.Position = UDim2.new(1, -60, 0, 10)
ToggleButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
ToggleButton.Text = "☰"
ToggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ToggleButton.Font = Enum.Font.GothamBold
ToggleButton.TextSize = 20
ToggleButton.Visible = false -- só aparece depois da key
ToggleButton.Parent = ScreenGui

local cornerToggle = Instance.new("UICorner")
cornerToggle.CornerRadius = UDim.new(1, 0)
cornerToggle.Parent = ToggleButton

-- Estado do Hub
local HubAberto = true

-- Função para abrir/fechar
local function ToggleHub()
    HubAberto = not HubAberto
    MainFrame.Visible = HubAberto
end

-- Clique no botão flutuante
ToggleButton.MouseButton1Click:Connect(ToggleHub)

-- Tecla K (PC)
UserInputService.InputBegan:Connect(function(input, gp)
    if not gp and input.KeyCode == Enum.KeyCode.K then
        ToggleHub()
    end
end)

-- Função para ativar o Hub (quando key aceita)
local function AtivarHub()
    KeyFrame.Visible = false
    MainFrame.Visible = true
    ToggleButton.Visible = true
end

-- Se já tem key salva e é válida → pular tela
if SavedKey then
    for _, k in ipairs(Keys) do
        if SavedKey == k then
            AtivarHub()
            return -- já abre direto
        end
    end
end

-- Lógica de Verificação da Key
CheckButton.MouseButton1Click:Connect(function()
    local userKey = KeyBox.Text
    local valid = false
    for _, k in ipairs(Keys) do
        if userKey == k then
            valid = true
            break
        end
    end

    if valid then
        StatusLabel.TextColor3 = Color3.fromRGB(100, 255, 100)
        StatusLabel.Text = "✅ Key aceita!"
        if writefile then
            writefile(SaveFile, userKey) -- salva a key no arquivo
        end
        wait(0.7)
        AtivarHub()
    else
        StatusLabel.TextColor3 = Color3.fromRGB(255, 100, 100)
        StatusLabel.Text = "❌ Key inválida!"
    end
end)
