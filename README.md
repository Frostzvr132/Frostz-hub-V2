local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()


-- Proteção contra Kick (versão segura)
local success, err = pcall(function()
    local mt = getrawmetatable(game)
    if not mt then return end
    
    setreadonly(mt, false)
    
    local oldNamecall = mt.__namecall
    mt.__namecall = newcclosure(function(self, ...)
        local method = getnamecallmethod()
        if tostring(method):lower() == "kick" then
            warn("Kick bloqueado!")
            return nil
        end
        return oldNamecall(self, ...)
    end)
    
    local oldIndex = mt.__index
    mt.__index = newcclosure(function(self, key)
        if tostring(key):lower() == "kick" then
            return function()
                warn("Kick bloqueado!")
            end
        end
        return oldIndex(self, key)
    end)
    
    setreadonly(mt, true)
end)

if not success then
    warn("Anti-kick não pôde ser aplicado:", err)
end


local Window = Rayfield:CreateWindow({
   Name = "Frostz Hub",
   Icon = nil, -- ou assetId válido em string
   LoadingTitle = "Beta V2",
   LoadingSubtitle = "by Viny",
   Theme = "Default",
   ToggleUIKeybind = "K",

   DisableRayfieldPrompts = false,
   DisableBuildWarnings = false,

   ConfigurationSaving = {
      Enabled = true,
      FolderName = nil,
      FileName = "Frostz Hub"
   },

   Discord = {
      Enabled = true,
      Invite = "https://discord.gg/KdePM6HQh4",
      RememberJoins = true
   },

   KeySystem = true,
   KeySettings = {
      Title = "Frostz Keys",
      Subtitle = "Key System",
      Note = "Para conseguir a key, entre no discord do Frostz Hub",
      FileName = "Key",
      SaveKey = true,
      GrabKeyFromSite = false,
      Key = {"Frostz Hub", "Viny", "Frostz Fire"}
   }
})

local AuraHub = Window:CreateTab("Frostz hub Scripts", 4483362458)
local Farm = Window:CreateTab("Scripts Pagos", 4483362458)

local SectionMain = AuraHub:CreateSection("Funções Principais")

local function MatarJogador()
   local player = game.Players.LocalPlayer
   if player and player.Character and player.Character:FindFirstChild("Humanoid") then
      player.Character.Humanoid.Health = 0
   end
end

local Miranda Tween = Farm:CreateButton({
   Name = "Miranda Tween",
   Callback = function()
      loadstring(game:HttpGet("https://pastefy.app/mTbfVy0H/raw", true))()
   end
})

local Miranda Hop = Farm:CreateButton({
   Name = "Miranda Hop",
   Callback = function()
      loadstring(game:HttpGet("https://gist.githubusercontent.com/Kauaicaro10-12/a3a950be0b587bc41dd927713633005e/raw/79e5d795393de33181b889fe0d57fb56fd741df8/MIRANDAHOP23do07.lua"))()
   end
})

local Lennon = Farm:CreateButton({
   Name = "Lennon Tween",
   Callback = function()
      loadstring(game:HttpGet("https://pastefy.app/1FPEhJmq/raw"))()
   end
})

local SectionExtra = Farm:CreateSection("Extras")

local KeybindExample = Farm:CreateKeybind({
   Name = "Atalho de Teclado",
   CurrentKeybind = "F",
   HoldToInteract = false,
   Callback = function(Key)
      -- ação ao pressionar a tecla
   end
})

local ParagraphCreator = Farm:CreateParagraph({
   Title = "Criador",
   Content = "Frostz hub by viny"
})
