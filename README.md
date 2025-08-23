-- LocalScript (StarterGui)

local Players = game:GetService("Players")
local HttpService = game:GetService("HttpService")
local player = Players.LocalPlayer

-- Nome do arquivo (DataStore local exploit usa writefile/readfile)
local KeyFile = "FrostzHubKey.json"

-- Lista de keys válidas
local ValidKeys = {
	"Frostz Hub",
	"Viny",
	"Frostz Fire"
}

-- Função para salvar key
local function SaveKey(key)
	if writefile then
		writefile(KeyFile, HttpService:JSONEncode({Key = key}))
	end
end

-- Função para carregar key
local function LoadKey()
	if isfile and isfile(KeyFile) then
		local data = HttpService:JSONDecode(readfile(KeyFile))
		return data.Key
	end
	return nil
end

-- Cria ScreenGui
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "FrostzHub"
ScreenGui.Parent = player:WaitForChild("PlayerGui")
ScreenGui.ResetOnSpawn = false

-- Frame principal (Hub)
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

-- Adiciona borda RGB apenas no Hub
local Border = Instance.new("UIStroke")
Border.Thickness = 2
Border.Parent = MainFrame

spawn(function()
	local hue = 0
	while MainFrame and MainFrame.Parent do
		hue = (hue + 1) % 360
		Border.Color = Color3.fromHSV(hue/360, 1, 1)
		wait(0.03)
	end
end)

-- Label de título
local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, 0, 0, 40)
Title.BackgroundTransparency = 1
Title.Text = "⚡ Frostz Hub - Beta V2"
Title.Font = Enum.Font.GothamBold
Title.TextSize = 18
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Parent = MainFrame

-- Criador
local Criador = Instance.new("TextLabel")
Criador.Size = UDim2.new(1, -20, 0, 30)
Criador.Position = UDim2.new(0, 10, 1, -40)
Criador.BackgroundTransparency = 1
Criador.Text = "✨ Frostz Hub by Viny"
Criador.Font = Enum.Font.Gotham
Criador.TextSize = 14
Criador.TextColor3 = Color3.fromRGB(200, 200, 200)
Criador.Parent = MainFrame

-- Função criar botão
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


-- Função ESP Players
local function ESPPlayers()
	for _, plr in pairs(Players:GetPlayers()) do
		if plr ~= player and plr.Character and plr.Character:FindFirstChild("Head") then
			local head = plr.Character.Head
			if not head:FindFirstChild("ESP_Player") then
				local Billboard = Instance.new("BillboardGui")
				Billboard.Name = "ESP_Player"
				Billboard.Size = UDim2.new(0,100,0,30)
				Billboard.Adornee = head
				Billboard.AlwaysOnTop = true
				Billboard.Parent = head

				local Label = Instance.new("TextLabel")
				Label.Size = UDim2.new(1,0,1,0)
				Label.BackgroundTransparency = 1
				Label.Text = plr.Name
				Label.TextColor3 = Color3.fromRGB(0,255,0)
				Label.TextScaled = true
				Label.Font = Enum.Font.GothamBold
				Label.Parent = Billboard
			end
		end
	end
end

-- Criando botões do hub
CriarBotao("Miranda Tween", 1, function()
	loadstring(game:HttpGet("https://pastefy.app/mTbfVy0H/raw", true))()
end)
CriarBotao("Miranda Hop", 2, function()
	loadstring(game:HttpGet("https://gist.githubusercontent.com/Kauaicaro10-12/a3a950be0b587bc41dd927713633005e/raw/79e5d795393de33181b889fe0d57fb56fd741df8/MIRANDAHOP23do07.lua"))()
end)
CriarBotao("Lennon Tween", 3, function()
	loadstring(game:HttpGet("https://pastefy.app/1FPEhJmq/raw"))()
end)
CriarBotao("ESP Players", 4, ESPPlayers) -- botão ESP Players

-- Botão de abrir/fechar Hub (inicia invisível)
local ToggleButton = Instance.new("TextButton")
ToggleButton.Size = UDim2.new(0, 120, 0, 40)
ToggleButton.Position = UDim2.new(0, 20, 0.8, 0)
ToggleButton.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
ToggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ToggleButton.Text = "Abrir/Fechar Hub"
ToggleButton.Font = Enum.Font.GothamBold
ToggleButton.TextSize = 14
ToggleButton.Visible = false
ToggleButton.Parent = ScreenGui

local corner2 = Instance.new("UICorner")
corner2.CornerRadius = UDim.new(0, 10)
corner2.Parent = ToggleButton

ToggleButton.MouseButton1Click:Connect(function()
	MainFrame.Visible = not MainFrame.Visible
end)

-- Sistema de Key
local function CriarTelaKey()
	local KeyFrame = Instance.new("Frame")
	KeyFrame.Size = UDim2.new(0, 300, 0, 150)
	KeyFrame.Position = UDim2.new(0.5, -150, 0.5, -75)
	KeyFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
	KeyFrame.Parent = ScreenGui

	local corner = Instance.new("UICorner")
	corner.CornerRadius = UDim.new(0, 10)
	corner.Parent = KeyFrame

	local Title = Instance.new("TextLabel")
	Title.Size = UDim2.new(1, 0, 0, 30)
	Title.BackgroundTransparency = 1
	Title.Text = "🔑 Frostz Hub Key"
	Title.Font = Enum.Font.GothamBold
	Title.TextSize = 16
	Title.TextColor3 = Color3.fromRGB(255, 255, 255)
	Title.Parent = KeyFrame

	local Box = Instance.new("TextBox")
	Box.Size = UDim2.new(0.8, 0, 0, 30)
	Box.Position = UDim2.new(0.1, 0, 0.4, 0)
	Box.PlaceholderText = "Digite sua key aqui"
	Box.Text = ""
	Box.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	Box.TextColor3 = Color3.fromRGB(255, 255, 255)
	Box.Font = Enum.Font.Gotham
	Box.TextSize = 14
	Box.Parent = KeyFrame

	local boxCorner = Instance.new("UICorner")
	boxCorner.CornerRadius = UDim.new(0, 6)
	boxCorner.Parent = Box

	local Confirm = Instance.new("TextButton")
	Confirm.Size = UDim2.new(0.5, 0, 0, 30)
	Confirm.Position = UDim2.new(0.25, 0, 0.7, 0)
	Confirm.Text = "Confirmar"
	Confirm.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
	Confirm.TextColor3 = Color3.fromRGB(255, 255, 255)
	Confirm.Font = Enum.Font.GothamBold
	Confirm.TextSize = 14
	Confirm.Parent = KeyFrame

	local confirmCorner = Instance.new("UICorner")
	confirmCorner.CornerRadius = UDim.new(0, 8)
	confirmCorner.Parent = Confirm

	Confirm.MouseButton1Click:Connect(function()
		local key = Box.Text
		for _, v in pairs(ValidKeys) do
			if key == v then
				SaveKey(key)
				KeyFrame:Destroy()
				MainFrame.Visible = true
				ToggleButton.Visible = true -- aparece só depois da key válida
				return
			end
		end
		Box.Text = "❌ Key inválida!"
	end)
end

-- Verifica se já tem key salva
local SavedKey = LoadKey()
local isValid = false
if SavedKey then
	for _, v in pairs(ValidKeys) do
		if SavedKey == v then
			isValid = true
			break
		end
	end
end

if not isValid then
	CriarTelaKey()
else
	MainFrame.Visible = true
	ToggleButton.Visible = true
end
