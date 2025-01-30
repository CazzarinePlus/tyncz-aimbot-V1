--[[⊹˚₊‧───────────────‧₊˚⊹·͙⁺˚*•̩̩͙✩•̩̩͙*˚⁺‧͙⁺˚*•̩ ̩͙✩•̩̩͙*˚⁺‧͙⁺˚*•̩̩͙✩•̩̩͙*˚ ⁺‧͙⊹˚₊‧───────────────‧₊˚⊹

  ______ ______ __ __ __     
 / \ / \| \ | \ | \    
| ▓▓▓▓▓▓\ ______ ______ _______ | ▓▓▓▓▓▓\\▓▓______ ____ | ▓▓____ ______ _| ▓▓_   
| ▓▓ | ▓▓/ \ / \| \ | ▓▓__| ▓▓\\\| ▓▓ \ / \| ▓▓\  
| ▓▓ | ▓▓ ▓▓▓▓▓▓\ ▓▓▓▓▓▓\ ▓▓▓▓▓▓▓\ | ▓▓ ▓▓ ▓▓ ▓▓▓▓▓▓\▓▓▓▓\ ▓▓▓▓▓▓▓\ ▓▓▓▓▓▓\\▓▓▓▓▓▓  
| ▓▓ | ▓▓ ▓▓ | ▓▓ ▓▓ ▓▓ ▓▓ | ▓▓ | ▓▓▓▓▓▓▓▓ ▓▓ ▓▓ | ▓▓ | ▓▓ ▓▓ | ▓▓ ▓▓ | ▓▓ | ▓▓__
| ▓▓__/ ▓▓ ▓▓__/ ▓▓ ▓▓▓▓▓▓▓▓ ▓▓ | ▓▓ | ▓▓ | ▓▓ ▓▓ ▓▓ | ▓▓ | ▓▓ ▓▓__/ ▓▓ ▓▓__/ ▓▓ | ▓▓| \
 \▓▓ ▓▓ ▓▓ ▓▓\▓▓ \ ▓▓ | ▓▓ | ▓▓ | ▓▓ ▓▓ ▓▓ | ▓▓ | ▓▓ ▓▓ ▓▓\▓▓ ▓▓ \▓▓ ▓▓
  \▓▓▓▓▓▓| ▓▓▓▓▓▓▓ \▓▓▓▓▓▓▓\▓▓ \▓▓ \▓▓ \▓▓\▓▓\▓▓ \▓▓ \▓▓\▓▓▓▓▓▓▓ \▓▓▓▓▓▓ \▓▓▓▓
         | ▓▓                                                                                 
         | ▓▓                                                                                 
          \▓▓                                                                                 

༺☆༻____________☾✧ ✩ ✧☽____________༺☆༻༺☆༻____________☾✧ ✩ ✧☽____________༺☆༻

    ✨Estrutura Universal de Assistência de Mira✨
    Versão 1.9.5

    twix.cyou/pix
    twix.cyou/OpenAimbotV3rm

    Autor: ttwiz_z (ttwizz) <i@twix.cyou>
    Licença: MIT
    GitHub: https://github.com/ttwizz/Open-Aimbot

    Problemas: https://github.com/ttwizz/Open-Aimbot/issues
    Solicitações de pull: https://github.com/ttwizz/Open-Aimbot/pulls
    Discussões: https://github.com/ttwizz/Open-Aimbot/discussions

    Wiki: https://moderka.org/Open-Aimbot

    Trustpilot: https://www.trustpilot.com/review/moderka.org

•───────•°•❀•°•───────•୧‿̩͙ ˖︵ꕀ ⠀𓏶 ̣̣̥⠀ ꕀ︵˖ ̩͙‿୨•───────•°•❀•°•───────•]]


--! Depurador

DEBUG local = falso

se DEBUG então
    getfenv().getfenv = função()
        retornar setmetatable({}, {
            __index = função()
                retornar função()
                    retornar verdadeiro
                fim
            fim
        })
    fim
fim


--! Serviços

local HttpService = jogo:GetService("HttpService")
Jogadores locais = jogo:GetService("Jogadores")
local UserInputService = jogo:GetService("UserInputService")
local RunService = jogo:GetService("RunService")
TweenService local = jogo:GetService("TweenService")


--! Gerenciador de Interface

Configurações de IU locais = {
    Largura da guia = 160,
    Tamanho = { 580, 460 },
    Tema = "VSC Escuro Alto Contraste",
    Acrílico = falso,
    Transparência = verdadeiro,
    MinimizeKey = "Deslocamento Direito",
    ShowNotifications = verdadeiro,
    ShowWarnings = verdadeiro,
    RenderingMode = "Renderização escalonada",
    AutoImportação = verdadeiro
}

Gerenciador de Interface local = {}

função InterfaceManager:ImportSettings()
    pcall(função()
        se não DEBUG e getfenv().isfile e getfenv().readfile e getfenv().isfile("UISettings.ttwizz") e getfenv().readfile("UISettings.ttwizz") então
            para Chave, Valor em seguida, HttpService:JSONDecode(getfenv().readfile("UISettings.ttwizz")) faça
                UISettings[Chave] = Valor
            fim
        fim
    fim)
fim

função InterfaceManager:ExportSettings()
    pcall(função()
        se não DEBUG e getfenv().isfile e getfenv().readfile e getfenv().writefile então
            getfenv().writefile("UISettings.ttwizz", HttpService:JSONEncode(UISettings))
        fim
    fim)
fim

InterfaceManager:ImportSettings()

UISettings.__ÚLTIMA_EXECUÇÃO__ = os.date()
InterfaceManager:ExportSettings()


--! Manipulador de cores

Manipulador de cores local = {}

função ColorsHandler:PackColour(Cor)
    retornar typeof(Cor) == "Cor3" e { R = Cor.R * 255, G = Cor.G * 255, B = Cor.B * 255 } ou typeof(Cor) == "tabela" e Cor ou { R = 255, G = 255, B = 255 }
fim

função ColorsHandler:UnpackColour(Cor)
    retornar typeof(Cor) == "tabela" e Color3.fromRGB(Cor.R, Cor.G, Cor.B) ou typeof(Cor) == "Cor3" e Cor ou Color3.fromRGB(255, 255, 255)
fim


--! Importador de configuração

Configuração Importada local = {}

pcall(função()
    se não DEBUG e getfenv().isfile e getfenv().readfile e getfenv().isfile(string.format("%s.ttwizz", game.GameId)) e getfenv().readfile(string.format("%s.ttwizz", game.GameId)) e UISettings.AutoImport então
        ImportedConfiguration = HttpService:JSONDecode(getfenv().readfile(string.format("%s.ttwizz", game.GameId)))
        para Chave, Valor em seguida, ImportedConfiguration faça
            se Chave == "FoVColour" ou Chave == "NameESPOutlineColour" ou Chave == "ESPColour" então
                ImportedConfiguration[Chave] = ColorsHandler:UnpackColour(Valor)
            fim
        fim
    fim
fim)


--! Inicializador de configuração

Configuração local = {}

--? Robô de mira

Configuration.Aimbot = ImportedConfiguration["Aimbot"] ou falso
Configuration.OnePressAimingMode = ImportedConfiguration["OnePressAimingMode"] ou falso
Configuration.AimKey = ImportedConfiguration["AimKey"] ou "RMB"
Configuration.AimMode = ImportedConfiguration["AimMode"] ou "Câmera"
Configuration.SilentAimMethods = ImportedConfiguration["SilentAimMethods"] ou { "Mouse.Hit / Mouse.Target", "GetMouseLocation" }
Configuration.SilentAimChance = ImportedConfiguration["SilentAimChance"] ou 100
Configuration.OffAimbotAfterKill = ImportedConfiguration["OffAimbotAfterKill"] ou falso
Configuration.AimPartDropdownValues ​​= ImportedConfiguration["AimPartDropdownValues"] ou { "Cabeça", "HumanoidRootPart" }
Configuration.AimPart = ImportedConfiguration["AimPart"] ou "HumanoidRootPart"
Configuration.RandomAimPart = ImportedConfiguration["RandomAimPart"] ou falso

Configuration.UseOffset = ImportedConfiguration["UseOffset"] ou falso
Configuration.OffsetType = ImportedConfiguration["OffsetType"] ou "Estático"
Configuration.StaticOffsetIncrement = ImportedConfiguration["StaticOffsetIncrement"] ou 10
Configuration.DynamicOffsetIncrement = ImportedConfiguration["DynamicOffsetIncrement"] ou 10
Configuration.AutoOffset = ImportedConfiguration["AutoOffset"] ou falso
Configuration.MaxAutoOffset = ImportedConfiguration["MaxAutoOffset"] ou 50

Configuration.UseSensitivity = ImportedConfiguration["UseSensitivity"] ou falso
Configuration.Sensitivity = ImportedConfiguration["Sensibilidade"] ou 50
Configuration.UseNoise = ImportedConfiguration["UseNoise"] ou falso
Configuration.NoiseFrequency = ImportedConfiguration["NoiseFrequency"] ou 50

--? Robôs

Configuration.SpinBot = ImportedConfiguration["SpinBot"] ou falso
Configuration.OnePressSpinningMode = ImportedConfiguration["OnePressSpinningMode"] ou falso
Configuration.SpinKey = ImportedConfiguration["SpinKey"] ou "Q"
Configuration.SpinBotVelocity = ImportedConfiguration["SpinBotVelocity"] ou 50
Configuration.SpinPartDropdownValues ​​= ImportedConfiguration["SpinPartDropdownValues"] ou { "Cabeça", "HumanoidRootPart" }
Configuration.SpinPart = ImportedConfiguration["SpinPart"] ou "HumanoidRootPart"
Configuration.RandomSpinPart = ImportedConfiguration["RandomSpinPart"] ou falso

Configuration.TriggerBot = ImportedConfiguration["TriggerBot"] ou falso
Configuration.OnePressTriggeringMode = ImportedConfiguration["OnePressTriggeringMode"] ou falso
Configuration.SmartTriggerBot = ImportedConfiguration["SmartTriggerBot"] ou falso
Configuration.TriggerKey = ImportedConfiguration["TriggerKey"] ou "E"
Configuration.TriggerBotChance = ImportedConfiguration["TriggerBotChance"] ou 100

--? Verificações

Configuration.AliveCheck = ImportedConfiguration["AliveCheck"] ou falso
Configuration.GodCheck = ImportedConfiguration["GodCheck"] ou falso
Configuration.TeamCheck = ImportedConfiguration["TeamCheck"] ou falso
Configuration.FriendCheck = ImportedConfiguration["FriendCheck"] ou falso
Configuration.FollowCheck = ImportedConfiguration["FollowCheck"] ou falso
Configuration.VerifiedBadgeCheck = ImportedConfiguration["VerifiedBadgeCheck"] ou falso
Configuration.WallCheck = ImportedConfiguration["WallCheck"] ou falso
Configuration.WaterCheck = ImportedConfiguration["WaterCheck"] ou falso

Configuration.FoVCheck = ImportedConfiguration["FoVCheck"] ou falso
Configuration.FoVRadius = ImportedConfiguration["FoVRadius"] ou 100
Configuration.MagnitudeCheck = ImportedConfiguration["MagnitudeCheck"] ou falso
Configuration.TriggerMagnitude = ImportedConfiguration["TriggerMagnitude"] ou 500
Configuration.TransparencyCheck = ImportedConfiguration["TransparencyCheck"] ou falso
Configuration.IgnoredTransparency = ImportedConfiguration["IgnoredTransparency"] ou 0,5
Configuration.WhitelistedGroupCheck = ImportedConfiguration["WhitelistedGroupCheck"] ou falso
Configuration.WhitelistedGroup = ImportedConfiguration["WhitelistedGroup"] ou 0
Configuration.BlacklistedGroupCheck = ImportedConfiguration["BlacklistedGroupCheck"] ou falso
Configuration.BlacklistedGroup = ImportedConfiguration["BlacklistedGroup"] ou 0

Configuration.IgnoredPlayersCheck = ImportedConfiguration["IgnoredPlayersCheck"] ou falso
Configuration.IgnoredPlayersDropdownValues ​​= ImportedConfiguration["IgnoredPlayersDropdownValues"] ou {}
Configuration.IgnoredPlayers = ImportedConfiguration["IgnoredPlayers"] ou {}
Configuration.TargetPlayersCheck = ImportedConfiguration["TargetPlayersCheck"] ou falso
Configuration.TargetPlayersDropdownValues ​​= ImportedConfiguration["TargetPlayersDropdownValues"] ou {}
Configuration.TargetPlayers = ImportedConfiguration["TargetPlayers"] ou {}

Configuration.PremiumCheck = ImportedConfiguration["PremiumCheck"] ou falso

--? Visuais

Configuration.FoV = ImportedConfiguration["FoV"] ou falso
Configuration.FoVKey = ImportedConfiguration["FoVKey"] ou "R"
Configuration.FoVThickness = ImportedConfiguration["FoVThickness"] ou 2
Configuration.FoVOpacity = ImportedConfiguration["FoVOpacity"] ou 0,8
Configuration.FoVFilled = ImportedConfiguration["FoVFilled"] ou falso
Configuration.FoVClour = ImportedConfiguration["FoVClour"] ou Color3.fromRGB(255, 255, 255)

Configuration.SmartESP = ImportedConfiguration["SmartESP"] ou falso
Configuration.ESPKey = ImportedConfiguration["ESPKey"] ou "T"
Configuration.ESPBox = ImportedConfiguration["ESPBox"] ou falso
Configuration.ESPBoxFilled = ImportedConfiguration["ESPBoxFilled"] ou falso
Configuration.NameESP = ImportedConfiguration["NameESP"] ou falso
Configuration.NameESPFont = ImportedConfiguration["NameESPFont"] ou "Monospace"
Configuration.NameESPSize = ImportedConfiguration["NameESPSize"] ou 16
Configuration.NameESPOutlineColour = ImportedConfiguration["NameESPOutlineColour"] ou Color3.fromRGB(0, 0, 0)
Configuration.HealthESP = ImportedConfiguration["HealthESP"] ou falso
Configuration.MagnitudeESP = ImportedConfiguration["MagnitudeESP"] ou falso
Configuration.TracerESP = ImportedConfiguration["TracerESP"] ou falso
Configuration.ESPThickness = ImportedConfiguration["ESPThickness"] ou 2
Configuration.ESPOpacity = ImportedConfiguration["ESPOpacity"] ou 0,8
Configuration.ESPCour = ImportedConfiguration["ESPCour"] ou Color3.fromRGB(255, 255, 255)
Configuration.ESPUseTeamColour = ImportedConfiguration["ESPUseTeamColour"] ou falso

Configuration.RainbowVisuals = ImportedConfiguration["RainbowVisuals"] ou falso
Configuration.RainbowDelay = ImportedConfiguration["RainbowDelay"] ou 5


--! Constantes

Jogador local = Jogadores.JogadorLocal
Mouse local = Jogador:ObterMouse()
local IsComputer = UserInputService.KeyboardEnabled e UserInputService.MouseEnabled

Etiquetas mensais locais = { "🎅%s❄️", "☃️%s🏂", "🌷%s☘️", "🌺%s🎀", "🐝%s🌼", "🌈%s😎", "🌞%s🏖️", "☀️%s💐", "🌦%s🍁", "🎃%s💀", "🍂%s☕", "🎄%s🎁" }
Etiquetas Premium locais = { "💫PREMIUM💫", "✨PREMIUM✨", "🌟PREMIUM🌟", "⭐PREMIUM⭐", "🤩PREMIUM🤩" }


--! Manipulador de nomes

função local GetPlayerName(String)
    se typeof(String) == "string" e #String > 0 então
        para _, _Player em seguida, Players:GetPlayers() faça
            se string.sub(string.lower(_Player.Name), 1, #string.lower(String)) == string.lower(String) então
                retornar _Player.Name
            fim
        fim
    fim
    retornar ""
fim


--! Campos

Status local = ""

local Fluente = nulo
ShowWarning local = falso

RobloxActive local = verdadeiro
Relógio local = os.clock()

local Aiming = falso
Alvo local = nulo
Tween local = nulo
Sensibilidade do Mouse local = UserInputService.Sensibilidade do MouseDelta

local Spinning = falso
Disparo local = falso
Campo de visão local = falso
local MostrandoESP = falso

fazer
    se typeof(script) == "Instância" e script:FindFirstChild("Fluente") e script:FindFirstChild("Fluente"):IsA("ModuleScript") então
        Fluente = require(script:FindFirstChild("Fluente"))
    outro
        Sucesso local, Resultado = pcall(function()
            retornar jogo:HttpGet("https://twix.cyou/Fluent.txt", true)
        fim)
        se Sucesso e typeof(Resultado) == "string" e string.find(Resultado, "dawid") então
            Fluente = getfenv().loadstring(Resultado)()
            se Fluent.Premium então
                retornar getfenv().loadstring(jogo:HttpGet("https://twix.cyou/Aimbot.txt", verdadeiro))()
            fim
            Sucesso local, Resultado = pcall(function()
                retornar jogo:HttpGet("https://twix.cyou/AimbotStatus.json", true)
            fim)
            se Success e typeof(Result) == "string" e pcall(HttpService.JSONDecode, HttpService, Result) e typeof(HttpService:JSONDecode(Result).message) == "string" então
                Status = HttpService:JSONDecode(Resultado).mensagem
            fim
        outro
            retornar
        fim
    fim
fim

Sensibilidade local alterada; Sensibilidade alterada = UserInputService:GetPropertyChangedSignal("MouseDeltaSensitivity"):Connect(function()
    se não for fluente então
        SensibilidadeAlterada:Desconectar()
    elseif não Aiming ou não DEBUG e (getfenv().mousemoverel e IsComputer e Configuration.AimMode == "Mouse" ou getfenv().hookmetamethod e getfenv().newcclosure e getfenv().checkcaller e getfenv().getnamecallmethod e Configuration.AimMode == "Silent") então
        MouseSensitivity = UserInputService.MouseDeltaSensitivity
    fim
fim)


--! Inicializador de UI

fazer
    Janela local = Fluente:CriarJanela({
        Título = string.format("%s <b><i>%s</i></b>", string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot"), #Status > 0 e Status ou "🔥GRÁTIS🔥"),
        Subtítulo = "Por @ttwiz_z",
        TabWidth = Configurações de interface do usuário.TabWidth,
        Tamanho = UDim2.fromOffset(table.unpack(UISettings.Size)),
        Tema = UISettings.Theme,
        Acrílico = UISettings.Acrílico,
        MinimizeKey = Configurações de UI.MinimizeKey
    })

    Guias locais = { Aimbot = Janela:AddTab({ Título = "Aimbot", Ícone = "mira" }) }

    Janela:SelecionarGuia(1)

    Guias.Aimbot:AddParagraph({
        Título = string.format("%s 🔥GRÁTIS🔥", string.format(RótulosMensais[os.date("*t").mês], "Abrir Aimbot")),
        Conteúdo = "✨Estrutura Universal de Assistência de Mira✨\nhttps://github.com/ttwizz/Open-Aimbot"
    })

    local AimbotSection = Tabs.Aimbot:AddSection("Aimbot")

    local AimbotToggle = AimbotSection:AddToggle("Aimbot", { Title = "Aimbot", Description = "Alterna o Aimbot", Default = Configuration.Aimbot })
    AimbotToggle:OnChanged(função(Valor)
        Configuração.Aimbot = Valor
        se não IsComputer então
            Objetivo = Valor
        fim
    fim)

    se IsComputer então
        local OnePressAimingModeToggle = AimbotSection:AddToggle("OnePressAimingMode", { Title = "Modo One-Press", Description = "Usa o Modo One-Press em vez do Modo de espera", Padrão = Configuration.OnePressAimingMode })
        OnePressAimingModeToggle:OnChanged(função(Valor)
            Configuration.OnePressAimingMode = Valor
        fim)

        AimKeybind local = AimbotSection:AddKeybind("AimKey", {
            Título = "Chave de mira",
            Descrição = "Altera a tecla de mira",
            Padrão = Configuration.AimKey,
            ChangedCallback = função(Valor)
                Configuração.AimKey = Valor
            fim
        })
        Configuration.AimKey = AimKeybind.Value ~= "RMB" e Enum.KeyCode[AimKeybind.Value] ou Enum.UserInputType.MouseButton2
    fim

    local AimModeDropdown = AimbotSection:AddDropdown("AimMode", {
        Título = "Modo de mira",
        Descrição = "Altera o Modo de Mira",
        Valores = { "Câmera" },
        Padrão = Configuration.AimMode,
        Retorno de chamada = função(Valor)
            Configuration.AimMode = Valor
        fim
    })
    se getfenv().mousemoverel e IsComputer então
        tabela.insert(AimModeDropdown.Values, "Mouse")
        AimModeDropdown:BuildDropdownList()
    outro
        ShowWarning = verdadeiro
    fim
    se getfenv().hookmetamethod e getfenv().newcclosure e getfenv().checkcaller e getfenv().getnamecallmethod então
        tabela.insert(AimModeDropdown.Values, "Silencioso")
        AimModeDropdown:BuildDropdownList()

        local SilentAimMethodsDropdown = AimbotSection:AddDropdown("MétodosSilentAim", {
            Título = "Métodos de mira silenciosa",
            Descrição = "Define os métodos de mira silenciosa",
            Valores = { "Mouse.Hit / Mouse.Target", "GetMouseLocation", "Raycast", "FindPartOnRay", "FindPartOnRayWithIgnoreList", "FindPartOnRayWithWhitelist" },
            Multi = verdadeiro,
            Padrão = Configuration.SilentAimMethods
        })
        SilentAimMethodsDropdown:OnChanged(função(Valor)
            Configuração.SilentAimMethods = {}
            para Chave, _ em seguida, Valor faça
                se typeof(Key) == "string" então
                    tabela.insert(Configuração.SilentAimMethods, Chave)
                fim
            fim
        fim)

        AimbotSection:AddSlider("ChanceDeAimSilencioso", {
            Título = "Chance de mira silenciosa",
            Descrição = "Altera a chance de acerto para mira silenciosa",
            Padrão = Configuration.SilentAimChance,
            Mín = 1,
            Máx = 100,
            Arredondamento = 1,
            Retorno de chamada = função(Valor)
                Configuração.SilentAimChance = Valor
            fim
        })
    outro
        ShowWarning = verdadeiro
    fim

    local OffAimbotAfterKillToggle = AimbotSection:AddToggle("OffAimbotAfterKill", { Title = "Desligado após matar", Description = "Desativa o modo de mira após matar um alvo", Default = Configuration.OffAimbotAfterKill })
    OffAimbotAfterKillToggle:OnChanged(função(Valor)
        Configuração.OffAimbotAfterKill = Valor
    fim)

    local AimPartDropdown = AimbotSection:AddDropdown("AimPart", {
        Título = "Parte do Objetivo",
        Descrição = "Altera a parte da mira",
        Valores = Configuration.AimPartDropdownValues,
        Padrão = Configuration.AimPart,
        Retorno de chamada = função(Valor)
            Configuração.AimPart = Valor
        fim
    })

    local RandomAimPartToggle = AimbotSection:AddToggle("RandomAimPart", { Title = "Parte de mira aleatória", Description = "Seleciona a cada segundo uma parte de mira aleatória no menu suspenso", Default = Configuration.RandomAimPart })
    RandomAimPartToggle:OnChanged(função(Valor)
        Configuração.RandomAimPart = Valor
    fim)

    AimbotSection:AddInput("AdicionarParteAim", {
        Título = "Adicionar parte do objetivo",
        Descrição = "Após digitar, pressione Enter",
        Concluído = verdadeiro,
        Espaço reservado = "Nome da peça",
        Retorno de chamada = função(Valor)
            se #Value > 0 e não table.find(Configuration.AimPartDropdownValues, Value) então
                tabela.insert(Configuração.AimPartDropdownValues, Valor)
                AimPartDropdown:SetValue(Valor)
            fim
        fim
    })

    AimbotSection:AddInput("RemoverAimPart", {
        Título = "Remover parte do objetivo",
        Descrição = "Após digitar, pressione Enter",
        Concluído = verdadeiro,
        Espaço reservado = "Nome da peça",
        Retorno de chamada = função(Valor)
            se #Value > 0 e table.find(Configuration.AimPartDropdownValues, Value) então
                se Configuration.AimPart == Valor então
                    AimPartDropdown:DefinirValor(nulo)
                fim
                tabela.remove(Configuração.AimPartDropdownValues, tabela.find(Configuração.AimPartDropdownValues, Valor))
                AimPartDropdown:SetValues(Configuração.AimPartDropdownValues)
            fim
        fim
    })

    AimbotSection:AdicionarBotão({
        Título = "Limpar todos os itens",
        Descrição = "Remove todos os elementos",
        Retorno de chamada = função()
            Itens locais = #Configuration.AimPartDropdownValues
            AimPartDropdown:DefinirValor(nulo)
            Configuração.AimPartDropdownValues ​​= {}
            AimPartDropdown:SetValues(Configuração.AimPartDropdownValues)
            Janela:Diálogo({
                Título = string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot"),
                Conteúdo = Itens == 0 e "Nada foi limpo!" ou Itens == 1 e "1 item foi limpo!" ou string.format("%s itens foram limpos!", Itens),
                Botões = {
                    {
                        Título = "Confirmar"
                    }
                }
            })
        fim
    })

    local AimOffsetSection = Tabs.Aimbot:AddSection("Deslocamento de mira")

    local UseOffsetToggle = AimOffsetSection:AddToggle("UseOffset", { Title = "Usar Offset", Description = "Alterna o Offset", Default = Configuration.UseOffset })
    UseOffsetToggle:OnChanged(função(Valor)
        Configuração.UseOffset = Valor
    fim)

    AimOffsetSection:AddDropdown("Tipo de Deslocamento", {
        Título = "Tipo de deslocamento",
        Descrição = "Altera o tipo de deslocamento",
        Valores = { "Estático", "Dinâmico", "Estático e Dinâmico" },
        Padrão = Configuration.OffsetType,
        Retorno de chamada = função(Valor)
            Configuração.OffsetType = Valor
        fim
    })

    AimOffsetSection:AddSlider("Incremento de Offset Estático", {
        Título = "Incremento de deslocamento estático",
        Descrição = "Altera o incremento de deslocamento estático",
        Padrão = Configuration.StaticOffsetIncrement,
        Mín = 1,
        Máx = 50,
        Arredondamento = 1,
        Retorno de chamada = função(Valor)
            Configuration.StaticOffsetIncrement = Valor
        fim
    })

    AimOffsetSection:AddSlider("Incremento de Offset Dinâmico", {
        Título = "Incremento de deslocamento dinâmico",
        Descrição = "Altera o incremento de deslocamento dinâmico",
        Padrão = Configuration.DynamicOffsetIncrement,
        Mín = 1,
        Máx = 50,
        Arredondamento = 1,
        Retorno de chamada = função(Valor)
            Configuration.DynamicOffsetIncrement = Valor
        fim
    })

    local AutoOffsetToggle = AimOffsetSection:AddToggle("AutoOffset", { Título = "Deslocamento automático", Descrição = "Alterna o deslocamento automático", Padrão = Configuration.AutoOffset })
    AutoOffsetToggle:OnChanged(função(Valor)
        Configuração.AutoOffset = Valor
    fim)

    AimOffsetSection:AddSlider("Deslocamento Automático Máximo", {
        Título = "Deslocamento automático máximo",
        Descrição = "Altera o deslocamento automático máximo",
        Padrão = Configuration.MaxAutoOffset,
        Mín = 1,
        Máx = 50,
        Arredondamento = 1,
        Retorno de chamada = função(Valor)
            Configuração.MaxAutoOffset = Valor
        fim
    })

    Sensibilidade localNoiseSection = Tabs.Aimbot:AddSection("Sensibilidade e Ruído")

    local UseSensitivityToggle = SensitivityNoiseSection:AddToggle("UseSensitivity", { Title = "Usar sensibilidade", Description = "Alterna a sensibilidade", Default = Configuration.UseSensitivity })
    UseSensitivityToggle:OnChanged(função(Valor)
        Configuration.UseSensitivity = Valor
    fim)

    SensibilidadeRuídoSeção:AddSlider("Sensibilidade", {
        Título = "Sensibilidade",
        Descrição = "Suaviza os movimentos do mouse/câmera ao mirar",
        Padrão = Configuração.Sensibilidade,
        Mín = 1,
        Máx = 100,
        Arredondamento = 1,
        Retorno de chamada = função(Valor)
            Configuração.Sensibilidade = Valor
        fim
    })

    local UseNoiseToggle = SensitivityNoiseSection:AddToggle("UseNoise", { Title = "Usar ruído", Description = "Alterna a vibração da câmera ao mirar", Default = Configuration.UseNoise })
    UseNoiseToggle:OnChanged(função(Valor)
        Configuração.UseNoise = Valor
    fim)

    SensibilidadeRuídoSeção:AddSlider("Frequência de Ruído", {
        Título = "Frequência de ruído",
        Descrição = "Altera a frequência do ruído",
        Padrão = Configuration.NoiseFrequency,
        Mín = 1,
        Máx = 100,
        Arredondamento = 1,
        Retorno de chamada = função(Valor)
            Configuration.NoiseFrequency = Valor
        fim
    })

    Tabs.Bots = Janela:AddTab({ Título = "Bots", Ícone = "bot" })

    Guias.Bots:AddParagraph({
        Título = string.format("%s 🔥GRÁTIS🔥", string.format(RótulosMensais[os.date("*t").mês], "Abrir Aimbot")),
        Conteúdo = "✨Estrutura Universal de Assistência de Mira✨\nhttps://github.com/ttwizz/Open-Aimbot"
    })

    Seção SpinBot local = Tabs.Bots:AddSection("SpinBot")

    SpinBotSection:AdicionarParágrafo({
        Título = "NOTA",
        Conteúdo = "O SpinBot não funciona normalmente no Modo de Renderização RenderStepped. Defina um valor de Modo de Renderização diferente de RenderStepped para resolver este problema."
    })

    local SpinBotToggle = SpinBotSection:AddToggle("SpinBot", { Título = "SpinBot", Descrição = "Alterna o SpinBot", Padrão = Configuration.SpinBot })
    SpinBotToggle:OnChanged(função(Valor)
        Configuração.SpinBot = Valor
        se não IsComputer então
            Girando = Valor
        fim
    fim)

    se IsComputer então
        local OnePressSpinningModeToggle = SpinBotSection:AddToggle("OnePressSpinningMode", { Title = "Modo One-Press", Description = "Usa o Modo One-Press em vez do Modo de espera", Padrão = Configuration.OnePressSpinningMode })
        OnePressSpinningModeToggle:OnChanged(função(Valor)
            Configuration.OnePressSpinningMode = Valor
        fim)

        local SpinKeybind = SpinBotSection:AddKeybind("SpinKey", {
            Título = "Girar Chave",
            Descrição = "Altera a tecla de rotação",
            Padrão = Configuration.SpinKey,
            ChangedCallback = função(Valor)
                Configuração.SpinKey = Valor
            fim
        })
        Configuration.SpinKey = SpinKeybind.Value ~= "RMB" e Enum.KeyCode[SpinKeybind.Value] ou Enum.UserInputType.MouseButton2
    fim

    SpinBotSection:AddSlider("Velocidade do SpinBot", {
        Título = "Velocidade do SpinBot",
        Descrição = "Altera a velocidade do SpinBot",
        Padrão = Configuration.SpinBotVelocity,
        Mín = 1,
        Máx = 50,
        Arredondamento = 1,
        Retorno de chamada = função(Valor)
            Configuração.SpinBotVelocity = Valor
        fim
    })

    local SpinPartDropdown = SpinBotSection:AddDropdown("SpinPart", {
        Título = "Parte de rotação",
        Descrição = "Altera a parte de rotação",
        Valores = Configuration.SpinPartDropdownValues,
        Padrão = Configuration.SpinPart,
        Retorno de chamada = função(Valor)
            Configuração.SpinPart = Valor
        fim
    })

    local RandomSpinPartToggle = SpinBotSection:AddToggle("RandomSpinPart", { Title = "Parte de rotação aleatória", Description = "Seleciona a cada segundo uma parte de rotação aleatória no menu suspenso", Default = Configuration.RandomSpinPart })
    RandomSpinPartToggle:OnChanged(função(Valor)
        Configuração.RandomSpinPart = Valor
    fim)

    SpinBotSection:AddInput("AdicionarParteGirar", {
        Título = "Adicionar parte de rotação",
        Descrição = "Após digitar, pressione Enter",
        Concluído = verdadeiro,
        Espaço reservado = "Nome da peça",
        Retorno de chamada = função(Valor)
            se #Value > 0 e não table.find(Configuration.SpinPartDropdownValues, Value) então
                tabela.insert(Configuração.SpinPartDropdownValues, Valor)
                SpinPartDropdown:SetValue(Valor)
            fim
        fim
    })

    SpinBotSection:AddInput("RemoverParteSpin", {
        Título = "Remover parte de rotação",
        Descrição = "Após digitar, pressione Enter",
        Concluído = verdadeiro,
        Espaço reservado = "Nome da peça",
        Retorno de chamada = função(Valor)
            se #Value > 0 e table.find(Configuration.SpinPartDropdownValues, Value) então
                se Configuration.SpinPart == Valor então
                    SpinPartDropdown:DefinirValor(nulo)
                fim
                tabela.remove(Configuração.SpinPartDropdownValues, tabela.find(Configuração.SpinPartDropdownValues, Valor))
                SpinPartDropdown:SetValues(Configuração.SpinPartDropdownValues)
            fim
        fim
    })

    SpinBotSection:AdicionarBotão({
        Título = "Limpar todos os itens",
        Descrição = "Remove todos os elementos",
        Retorno de chamada = função()
            Itens locais = #Configuration.SpinPartDropdownValues
            SpinPartDropdown:DefinirValor(nulo)
            Configuração.SpinPartDropdownValues ​​= {}
            SpinPartDropdown:SetValues(Configuração.SpinPartDropdownValues)
            Janela:Diálogo({
                Título = string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot"),
                Conteúdo = Itens == 0 e "Nada foi limpo!" ou Itens == 1 e "1 item foi limpo!" ou string.format("%s itens foram limpos!", Itens),
                Botões = {
                    {
                        Título = "Confirmar"
                    }
                }
            })
        fim
    })

    se getfenv().mouse1click e IsComputer então
        TriggerBotSection local = Guias.Bots:AddSection("TriggerBot")

        local TriggerBotToggle = TriggerBotSection:AddToggle("TriggerBot", { Title = "TriggerBot", Description = "Alterna o TriggerBot", Default = Configuration.TriggerBot })
        TriggerBotToggle:OnChanged(função(Valor)
            Configuração.TriggerBot = Valor
        fim)

        local OnePressTriggeringModeToggle = TriggerBotSection:AddToggle("OnePressTriggeringMode", { Title = "Modo One-Press", Description = "Usa o Modo One-Press em vez do Modo de espera", Default = Configuration.OnePressTriggeringMode })
        OnePressTriggeringModeToggle:OnChanged(função(Valor)
            Configuration.OnePressTriggeringMode = Valor
        fim)

        local SmartTriggerBotToggle = TriggerBotSection:AddToggle("SmartTriggerBot", { Title = "Smart TriggerBot", Description = "Usa o TriggerBot somente ao mirar", Default = Configuration.SmartTriggerBot })
        SmartTriggerBotToggle:OnChanged(função(Valor)
            Configuração.SmartTriggerBot = Valor
        fim)

        local TriggerKeybind = TriggerBotSection:AddKeybind("TriggerKey", {
            Título = "Chave de gatilho",
            Descrição = "Altera a tecla de gatilho",
            Padrão = Configuração.TriggerKey,
            ChangedCallback = função(Valor)
                Configuração.TriggerKey = Valor
            fim
        })
        Configuration.TriggerKey = TriggerKeybind.Value ~= "RMB" e Enum.KeyCode[TriggerKeybind.Value] ou Enum.UserInputType.MouseButton2

        TriggerBotSection:AddSlider("Chance do TriggerBot", {
            Título = "Chance do TriggerBot",
            Descrição = "Altera a chance de acerto do TriggerBot",
            Padrão = Configuração.TriggerBotChance,
            Mín = 1,
            Máx = 100,
            Arredondamento = 1,
            Retorno de chamada = função(Valor)
                Configuração.TriggerBotChance = Valor
            fim
        })
    outro
        ShowWarning = verdadeiro
    fim

    Tabs.Checks = Window:AddTab({ Title = "Verificações", Icon = "list-checks" })

    Guias.Verificações:AddParagraph({
        Título = string.format("%s 🔥GRÁTIS🔥", string.format(RótulosMensais[os.date("*t").mês], "Abrir Aimbot")),
        Conteúdo = "✨Estrutura Universal de Assistência de Mira✨\nhttps://github.com/ttwizz/Open-Aimbot"
    })

    local SimpleChecksSection = Tabs.Checks:AddSection("Verificações Simples")

    local AliveCheckToggle = SimpleChecksSection:AddToggle("AliveCheck", { Title = "Verificação Alive", Description = "Alterna a verificação Alive", Default = Configuration.AliveCheck })
    AliveCheckToggle:OnChanged(função(Valor)
        Configuração.AliveCheck = Valor
    fim)

    local GodCheckToggle = SimpleChecksSection:AddToggle("GodCheck", { Título = "Verificação de Deus", Descrição = "Alterna a Verificação de Deus", Padrão = Configuration.GodCheck })
    GodCheckToggle:OnChanged(função(Valor)
        Configuração.GodCheck = Valor
    fim)

    local TeamCheckToggle = SimpleChecksSection:AddToggle("TeamCheck", { Title = "Verificação de equipe", Description = "Alterna a verificação de equipe", Default = Configuration.TeamCheck })
    TeamCheckToggle:OnChanged(função(Valor)
        Configuration.TeamCheck = Valor
    fim)

    local FriendCheckToggle = SimpleChecksSection:AddToggle("FriendCheck", { Title = "Verificação de amigo", Description = "Alterna a verificação de amigo", Default = Configuration.FriendCheck })
    FriendCheckToggle:OnChanged(função(Valor)
        Configuração.FriendCheck = Valor
    fim)

    local FollowCheckToggle = SimpleChecksSection:AddToggle("FollowCheck", { Title = "Verificação de acompanhamento", Description = "Alterna a verificação de acompanhamento", Default = Configuration.FollowCheck })
    FollowCheckToggle:OnChanged(função(Valor)
        Configuração.FollowCheck = Valor
    fim)

    local VerifiedBadgeCheckToggle = SimpleChecksSection:AddToggle("VerifiedBadgeCheck", { Title = "Verificação de selo verificado", Description = "Alterna a verificação de selo verificado", Default = Configuration.VerifiedBadgeCheck })
    VerifiedBadgeCheckToggle:OnChanged(função(Valor)
        Configuration.VerifiedBadgeCheck = Valor
    fim)

    local WallCheckToggle = SimpleChecksSection:AddToggle("WallCheck", { Title = "Verificação de parede", Description = "Alterna a verificação de parede", Default = Configuration.WallCheck })
    WallCheckToggle:OnChanged(função(Valor)
        Configuração.WallCheck = Valor
    fim)

    local WaterCheckToggle = SimpleChecksSection:AddToggle("WaterCheck", { Title = "Verificação de água", Description = "Alterna a verificação de água se a verificação de parede estiver habilitada", Default = Configuration.WaterCheck })
    WaterCheckToggle:OnChanged(função(Valor)
        Configuration.WaterCheck = Valor
    fim)

    local AdvancedChecksSection = Tabs.Checks:AddSection("Verificações avançadas")

    local FoVCheckToggle = AdvancedChecksSection:AddToggle("FoVCheck", { Title = "Verificação de FoV", Description = "Alterna a verificação de FoV", Default = Configuration.FoVCheck })
    FoVCheckToggle:OnChanged(função(Valor)
        Configuração.FoVCheck = Valor
    fim)

    Seção de Verificações Avançadas: Adicionar Controle Deslizante("FoVRadius", {
        Título = "Raio do campo de visão",
        Descrição = "Altera o raio do campo de visão",
        Padrão = Configuration.FoVRadius,
        Mínimo = 10,
        Máx = 1000,
        Arredondamento = 1,
        Retorno de chamada = função(Valor)
            Configuration.FoVRadius = Valor
        fim
    })

    local MagnitudeCheckToggle = AdvancedChecksSection:AddToggle("MagnitudeCheck", { Title = "Verificação de magnitude", Description = "Alterna a verificação de magnitude", Default = Configuration.MagnitudeCheck })
    MagnitudeCheckToggle:OnChanged(função(Valor)
        Configuração.MagnitudeCheck = Valor
    fim)

    AdvancedChecksSection:AddSlider("Magnitude do gatilho", {
        Título = "Magnitude do gatilho",
        Descrição = "Distância entre o personagem nativo e o personagem alvo",
        Padrão = Configuração.TriggerMagnitude,
        Mínimo = 10,
        Máx = 1000,
        Arredondamento = 1,
        Retorno de chamada = função(Valor)
            Configuração.TriggerMagnitude = Valor
        fim
    })

    local TransparencyCheckToggle = AdvancedChecksSection:AddToggle("TransparencyCheck", { Title = "Verificação de transparência", Description = "Alterna a verificação de transparência", Default = Configuration.TransparencyCheck })
    TransparencyCheckToggle:OnChanged(função(Valor)
        Configuration.TransparencyCheck = Valor
    fim)

    AdvancedChecksSection:AddSlider("Transparência ignorada", {
        Título = "Transparência ignorada",
        Descrição = "O alvo é ignorado se sua transparência for > que / = à definida",
        Padrão = Configuration.IgnoredTransparency,
        Mín = 0,1,
        Máx = 1,
        Arredondamento = 1,
        Retorno de chamada = função(Valor)
            Configuration.IgnoredTransparency = Valor
        fim
    })

    local WhitelistedGroupCheckToggle = AdvancedChecksSection:AddToggle("WhitelistedGroupCheck", { Title = "Verificação de grupo na lista de permissões", Description = "Alterna a verificação de grupo na lista de permissões", Default = Configuration.WhitelistedGroupCheck })
    WhitelistedGroupCheckToggle:OnChanged(função(Valor)
        Configuration.WhitelistedGroupCheck = Valor
    fim)

    AdvancedChecksSection:AddInput("Grupo na lista de permissões", {
        Título = "Grupo na lista de permissões",
        Descrição = "Após digitar, pressione Enter",
        Padrão = Configuration.WhitelistedGroup,
        Numérico = verdadeiro,
        Concluído = verdadeiro,
        Espaço reservado = "ID do grupo",
        Retorno de chamada = função(Valor)
            Configuration.WhitelistedGroup = #tostring(Value) > 0 e tonumber(Value) ou 0
        fim
    })

    local BlacklistedGroupCheckToggle = AdvancedChecksSection:AddToggle("BlacklistedGroupCheck", { Title = "Verificação de grupo na lista negra", Description = "Alterna a verificação de grupo na lista negra", Default = Configuration.BlacklistedGroupCheck })
    BlacklistedGroupCheckToggle:OnChanged(função(Valor)
        Configuration.BlacklistedGroupCheck = Valor
    fim)

    AdvancedChecksSection:AddInput("Grupo na lista negra", {
        Título = "Grupo na lista negra",
        Descrição = "Após digitar, pressione Enter",
        Padrão = Configuration.BlacklistedGroup,
        Numérico = verdadeiro,
        Concluído = verdadeiro,
        Espaço reservado = "ID do grupo",
        Retorno de chamada = função(Valor)
            Configuration.BlacklistedGroup = #tostring(Valor) > 0 e tonumber(Valor) ou 0
        fim
    })

    local ExpertChecksSection = Tabs.Checks:AddSection("Verificações de especialistas")

    local IgnoredPlayersCheckToggle = ExpertChecksSection:AddToggle("IgnoredPlayersCheck", { Title = "Verificação de jogadores ignorados", Description = "Alterna a verificação de jogadores ignorados", Default = Configuration.IgnoredPlayersCheck })
    IgnoredPlayersCheckToggle:OnChanged(função(Valor)
        Configuration.IgnoredPlayersCheck = Valor
    fim)

    local IgnoredPlayersDropdown = ExpertChecksSection:AddDropdown("Jogadores Ignorados", {
        Título = "Jogadores Ignorados",
        Descrição = "Define os jogadores ignorados",
        Valores = Configuration.IgnoredPlayersDropdownValues,
        Multi = verdadeiro,
        Padrão = Configuration.IgnoredPlayers
    })
    IgnoredPlayersDropdown:OnChanged(função(Valor)
        Configuração.IgnoredPlayers = {}
        para Chave, _ em seguida, Valor faça
            se typeof(Key) == "string" então
                tabela.insert(Configuração.IgnoredPlayers, Chave)
            fim
        fim
    fim)

    ExpertChecksSection:AddInput("AdicionarJogadorIgnorado", {
        Título = "Adicionar jogador ignorado",
        Descrição = "Após digitar, pressione Enter",
        Concluído = verdadeiro,
        Espaço reservado = "Nome do jogador",
        Retorno de chamada = função(Valor)
            Valor = #GetPlayerName(Valor) > 0 e GetPlayerName(Valor) ou pcall(Players.GetUserIdFromNameAsync, Jogadores, Valor) e pcall(Players.GetNameFromUserIdAsync, Jogadores, Jogadores:GetUserIdFromNameAsync(Valor)) e Jogadores:GetNameFromUserIdAsync(Jogadores:GetUserIdFromNameAsync(Valor)) ou string.sub(Valor, 1, 1) == "@" e (#GetPlayerName(string.sub(Valor, 2)) > 0 e GetPlayerName(string.sub(Valor, 2)) ou pcall(Players.GetUserIdFromNameAsync, Jogadores, string.sub(Valor, 2)) e pcall(Players.GetNameFromUserIdAsync, Jogadores, Jogadores:GetUserIdFromNameAsync(string.sub(Valor, 2))) e Jogadores:GetNameFromUserIdAsync(Jogadores:GetUserIdFromNameAsync(string.sub(Value, 2)))) ou string.sub(Value, 1, 1) == "#" e pcall(Jogadores.GetNameFromUserIdAsync, Jogadores, tonumber(string.sub(Value, 2))) e Jogadores:GetNameFromUserIdAsync(tonumber(string.sub(Value, 2))) ou ""
            se #Value > 0 e não table.find(Configuration.IgnoredPlayersDropdownValues, Value) então
                table.insert(Configuração.IgnoredPlayersDropdownValues, Valor)
                se não table.find(Configuration.IgnoredPlayers, Value) então
                    IgnoredPlayersDropdown.Value[Valor] = verdadeiro
                    tabela.insert(Configuração.IgnoredPlayers, Valor)
                fim
                IgnoredPlayersDropdown:BuildDropdownList()
            fim
        fim
    })

    ExpertChecksSection:AddInput("RemoverJogadorIgnorado", {
        Título = "Remover jogador ignorado",
        Descrição = "Após digitar, pressione Enter",
        Concluído = verdadeiro,
        Espaço reservado = "Nome do jogador",
        Retorno de chamada = função(Valor)
            Valor = #GetPlayerName(Valor) > 0 e GetPlayerName(Valor) ou pcall(Players.GetUserIdFromNameAsync, Jogadores, Valor) e pcall(Players.GetNameFromUserIdAsync, Jogadores, Jogadores:GetUserIdFromNameAsync(Valor)) e Jogadores:GetNameFromUserIdAsync(Jogadores:GetUserIdFromNameAsync(Valor)) ou string.sub(Valor, 1, 1) == "@" e (#GetPlayerName(string.sub(Valor, 2)) > 0 e GetPlayerName(string.sub(Valor, 2)) ou pcall(Players.GetUserIdFromNameAsync, Jogadores, string.sub(Valor, 2)) e pcall(Players.GetNameFromUserIdAsync, Jogadores, Jogadores:GetUserIdFromNameAsync(string.sub(Valor, 2))) e Jogadores:GetNameFromUserIdAsync(Jogadores:GetUserIdFromNameAsync(string.sub(Value, 2)))) ou string.sub(Value, 1, 1) == "#" e pcall(Jogadores.GetNameFromUserIdAsync, Jogadores, tonumber(string.sub(Value, 2))) e Jogadores:GetNameFromUserIdAsync(tonumber(string.sub(Value, 2))) ou ""
            se #Value > 0 e table.find(Configuration.IgnoredPlayersDropdownValues, Value) então
                se table.find(Configuration.IgnoredPlayers, Valor) então
                    IgnoredPlayersDropdown.Value[Valor] = nulo
                    tabela.remove(Configuração.IgnoredPlayers, tabela.find(Configuração.IgnoredPlayers, Valor))
                    IgnoredPlayersDropdown:Exibir()
                fim
                tabela.remove(Configuração.IgnoredPlayersDropdownValues, tabela.find(Configuração.IgnoredPlayersDropdownValues, Valor))
                IgnoredPlayersDropdown:DefinirValores(Configuração.IgnoredPlayersDropdownValues)
            fim
        fim
    })

    ExpertChecksSection:AdicionarBotão({
        Título = "Desmarcar todos os itens",
        Descrição = "Desmarca todos os elementos",
        Retorno de chamada = função()
            Itens locais = #Configuration.IgnoredPlayers
            IgnoredPlayersDropdown:DefinirValor({})
            Janela:Diálogo({
                Título = string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot"),
                Conteúdo = Itens == 0 e "Nada foi desmarcado!" ou Itens == 1 e "1 item foi desmarcado!" ou string.format("%s itens foram desmarcados!", Itens),
                Botões = {
                    {
                        Título = "Confirmar"
                    }
                }
            })
        fim
    })

    ExpertChecksSection:AdicionarBotão({
        Título = "Limpar itens não selecionados",
        Descrição = "Remove jogadores não selecionados",
        Retorno de chamada = função()
            Cache local = {}
            Itens locais = 0
            para _, Valor em próximo, Configuration.IgnoredPlayersDropdownValues ​​do
                se table.find(Configuration.IgnoredPlayers, Valor) então
                    tabela.insert(Cache, Valor)
                outro
                    Itens = Itens + 1
                fim
            fim
            Configuração.IgnoredPlayersDropdownValues ​​= Cache
            IgnoredPlayersDropdown:DefinirValores(Configuração.IgnoredPlayersDropdownValues)
            Janela:Diálogo({
                Título = string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot"),
                Conteúdo = Itens == 0 e "Nada foi limpo!" ou Itens == 1 e "1 item foi limpo!" ou string.format("%s itens foram limpos!", Itens),
                Botões = {
                    {
                        Título = "Confirmar"
                    }
                }
            })
        fim
    })

    local TargetPlayersCheckToggle = ExpertChecksSection:AddToggle("TargetPlayersCheck", { Title = "Verificação de jogadores-alvo", Description = "Alterna a verificação de jogadores-alvo", Default = Configuration.TargetPlayersCheck })
    TargetPlayersCheckToggle:OnChanged(função(Valor)
        Configuration.TargetPlayersCheck = Valor
    fim)

    local TargetPlayersDropdown = ExpertChecksSection:AddDropdown("TargetPlayers", {
        Título = "Jogadores Alvo",
        Descrição = "Define os jogadores alvo",
        Valores = Configuration.TargetPlayersDropdownValues,
        Multi = verdadeiro,
        Padrão = Configuration.TargetPlayers
    })
    TargetPlayersDropdown:OnChanged(função(Valor)
        Configuração.TargetPlayers = {}
        para Chave, _ em seguida, Valor faça
            se typeof(Key) == "string" então
                tabela.insert(Configuração.TargetPlayers, Chave)
            fim
        fim
    fim)

    ExpertChecksSection:AddInput("AdicionarJogadorAlvo", {
        Título = "Adicionar jogador alvo",
        Descrição = "Após digitar, pressione Enter",
        Concluído = verdadeiro,
        Espaço reservado = "Nome do jogador",
        Retorno de chamada = função(Valor)
            Valor = #GetPlayerName(Valor) > 0 e GetPlayerName(Valor) ou pcall(Players.GetUserIdFromNameAsync, Jogadores, Valor) e pcall(Players.GetNameFromUserIdAsync, Jogadores, Jogadores:GetUserIdFromNameAsync(Valor)) e Jogadores:GetNameFromUserIdAsync(Jogadores:GetUserIdFromNameAsync(Valor)) ou string.sub(Valor, 1, 1) == "@" e (#GetPlayerName(string.sub(Valor, 2)) > 0 e GetPlayerName(string.sub(Valor, 2)) ou pcall(Players.GetUserIdFromNameAsync, Jogadores, string.sub(Valor, 2)) e pcall(Players.GetNameFromUserIdAsync, Jogadores, Jogadores:GetUserIdFromNameAsync(string.sub(Valor, 2))) e Jogadores:GetNameFromUserIdAsync(Jogadores:GetUserIdFromNameAsync(string.sub(Value, 2)))) ou string.sub(Value, 1, 1) == "#" e pcall(Jogadores.GetNameFromUserIdAsync, Jogadores, tonumber(string.sub(Value, 2))) e Jogadores:GetNameFromUserIdAsync(tonumber(string.sub(Value, 2))) ou ""
            se #Value > 0 e não table.find(Configuration.TargetPlayersDropdownValues, Value) então
                table.insert(Configuração.TargetPlayersDropdownValues, Valor)
                se não table.find(Configuration.TargetPlayers, Value) então
                    TargetPlayersDropdown.Value[Valor] = verdadeiro
                    tabela.insert(Configuração.TargetPlayers, Valor)
                fim
                TargetPlayersDropdown:BuildDropdownList()
            fim
        fim
    })

    ExpertChecksSection:AddInput("Remover JogadorAlvo", {
        Título = "Remover jogador alvo",
        Descrição = "Após digitar, pressione Enter",
        Concluído = verdadeiro,
        Espaço reservado = "Nome do jogador",
        Retorno de chamada = função(Valor)
            Valor = #GetPlayerName(Valor) > 0 e GetPlayerName(Valor) ou pcall(Players.GetUserIdFromNameAsync, Jogadores, Valor) e pcall(Players.GetNameFromUserIdAsync, Jogadores, Jogadores:GetUserIdFromNameAsync(Valor)) e Jogadores:GetNameFromUserIdAsync(Jogadores:GetUserIdFromNameAsync(Valor)) ou string.sub(Valor, 1, 1) == "@" e (#GetPlayerName(string.sub(Valor, 2)) > 0 e GetPlayerName(string.sub(Valor, 2)) ou pcall(Players.GetUserIdFromNameAsync, Jogadores, string.sub(Valor, 2)) e pcall(Players.GetNameFromUserIdAsync, Jogadores, Jogadores:GetUserIdFromNameAsync(string.sub(Valor, 2))) e Jogadores:GetNameFromUserIdAsync(Jogadores:GetUserIdFromNameAsync(string.sub(Value, 2)))) ou string.sub(Value, 1, 1) == "#" e pcall(Jogadores.GetNameFromUserIdAsync, Jogadores, tonumber(string.sub(Value, 2))) e Jogadores:GetNameFromUserIdAsync(tonumber(string.sub(Value, 2))) ou ""
            se #Value > 0 e table.find(Configuration.TargetPlayersDropdownValues, Value) então
                se table.find(Configuration.TargetPlayers, Valor) então
                    TargetPlayersDropdown.Value[Valor] = nulo
                    tabela.remove(Configuração.TargetPlayers, tabela.find(Configuração.TargetPlayers, Valor))
                    TargetPlayersDropdown:Exibir()
                fim
                tabela.remove(Configuração.TargetPlayersDropdownValues, tabela.find(Configuração.TargetPlayersDropdownValues, Valor))
                TargetPlayersDropdown:DefinirValores(Configuração.TargetPlayersDropdownValues)
            fim
        fim
    })

    ExpertChecksSection:AdicionarBotão({
        Título = "Desmarcar todos os itens",
        Descrição = "Desmarca todos os elementos",
        Retorno de chamada = função()
            Itens locais = #Configuration.TargetPlayers
            TargetPlayersDropdown:DefinirValor({})
            Janela:Diálogo({
                Título = string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot"),
                Conteúdo = Itens == 0 e "Nada foi desmarcado!" ou Itens == 1 e "1 item foi desmarcado!" ou string.format("%s itens foram desmarcados!", Itens),
                Botões = {
                    {
                        Título = "Confirmar"
                    }
                }
            })
        fim
    })

    ExpertChecksSection:AdicionarBotão({
        Título = "Limpar itens não selecionados",
        Descrição = "Remove jogadores não selecionados",
        Retorno de chamada = função()
            Cache local = {}
            Itens locais = 0
            para _, Valor em próximo, Configuration.TargetPlayersDropdownValues ​​do
                se table.find(Configuration.TargetPlayers, Valor) então
                    tabela.insert(Cache, Valor)
                outro
                    Itens = Itens + 1
                fim
            fim
            Configuração.TargetPlayersDropdownValues ​​= Cache
            TargetPlayersDropdown:DefinirValores(Configuração.TargetPlayersDropdownValues)
            Janela:Diálogo({
                Título = string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot"),
                Conteúdo = Itens == 0 e "Nada foi limpo!" ou Itens == 1 e "1 item foi limpo!" ou string.format("%s itens foram limpos!", Itens),
                Botões = {
                    {
                        Título = "Confirmar"
                    }
                }
            })
        fim
    })

    local PremiumChecksSection = Tabs.Checks:AddSection("Cheques Premium")

    local PremiumCheckToggle = PremiumChecksSection:AddToggle("PremiumCheck", { Title = "Verificação Premium", Description = "Alterna a Verificação Premium", Default = Configuration.PremiumCheck })
    PremiumCheckToggle:OnChanged(função(Valor)
        Configuração.PremiumCheck = Valor
    fim)

    PremiumChecksSection:AddParagraph({
        Título = string.format("%s 💫PREMIUM💫", string.format(RótulosMensais[os.date("*t").mês], "Abrir Aimbot")),
        Conteúdo = "✨Atualize para desbloquear todas as opções✨\nEntre em contato com @ttwiz_z via Discord para comprar"
    })

    se DEBUG ou getfenv().Drawing e getfenv().Drawing.new então
        Tabs.Visuals = Janela:AddTab({ Título = "Visuals", Ícone = "caixa" })

        Guias.Visuais:AddParagraph({
            Título = string.format("%s 🔥GRÁTIS🔥", string.format(RótulosMensais[os.date("*t").mês], "Abrir Aimbot")),
            Conteúdo = "✨Estrutura Universal de Assistência de Mira✨\nhttps://github.com/ttwizz/Open-Aimbot"
        })

        FoVSection local = Guias.Visuais:AddSection("FoV")

        local FoVToggle = FoVSection:AddToggle("FoV", { Title = "FoV", Description = "Exibe graficamente o raio do FoV", Default = Configuration.FoV })
        FoVToggle:OnChanged(função(Valor)
            Configuração.FoV = Valor
            se não IsComputer então
                MostrandoFoV = Valor
            fim
        fim)

        se IsComputer então
            local FoVKeybind = FoVSection:AddKeybind("FoVKey", {
                Título = "Chave FoV",
                Descrição = "Altera a chave do campo de visão",
                Padrão = Configuration.FoVKey,
                ChangedCallback = função(Valor)
                    Configuration.FoVKey = Valor
                fim
            })
            Configuration.FoVKey = FoVKeybind.Value ~= "RMB" e Enum.KeyCode[FoVKeybind.Value] ou Enum.UserInputType.MouseButton2
        fim

        FoVSection:AddSlider("Espessura do FoV", {
            Título = "Espessura do campo de visão",
            Descrição = "Altera a espessura do campo de visão",
            Padrão = Configuration.FoVThickness,
            Mín = 1,
            Máx = 10,
            Arredondamento = 1,
            Retorno de chamada = função(Valor)
                Configuração.FoVThickness = Valor
            fim
        })

        FoVSection:AddSlider("FoVOpacidade", {
            Título = "Opacidade do FoV",
            Descrição = "Altera a opacidade do campo de visão",
            Padrão = Configuração.FoVOpacidade,
            Mín = 0,1,
            Máx = 1,
            Arredondamento = 1,
            Retorno de chamada = função(Valor)
                Configuração.FoVOpacidade = Valor
            fim
        })

        local FoVFilledToggle = FoVSection:AddToggle("FoVFilled", { Title = "FoV preenchido", Description = "Torna o FoV preenchido", Default = Configuration.FoVFilled })
        FoVFilledToggle:OnChanged(função(Valor)
            Configuration.FoVFilled = Valor
        fim)

        FoVSection:AddColorpicker("FoVColour", {
            Título = "Cor do campo de visão",
            Descrição = "Altera a cor do campo de visão",
            Padrão = Configuration.FoVClour,
            Retorno de chamada = função(Valor)
                Configuração.FoVClour = Valor
            fim
        })

        ESPSection local = Guias.Visuais:AddSection("ESP")

        local SmartESPToggle = ESPSection:AddToggle("SmartESP", { Title = "Smart ESP", Description = "Não ESP os jogadores da lista de permissões", Default = Configuration.SmartESP })
        SmartESPToggle:OnChanged(função(Valor)
            Configuração.SmartESP = Valor
        fim)

        se IsComputer então
            ESPKeybind local = ESPSection:AddKeybind("ESPKey", {
                Título = "Chave ESP",
                Descrição = "Altera a chave ESP",
                Padrão = Configuration.ESPKey,
                ChangedCallback = função(Valor)
                    Configuração.ESPKey = Valor
                fim
            })
            Configuration.ESPKey = ESPKeybind.Value ~= "RMB" e Enum.KeyCode[ESPKeybind.Value] ou Enum.UserInputType.MouseButton2
        fim

        local ESPBoxToggle = ESPSection:AddToggle("ESPBox", { Title = "ESP Box", Description = "Cria a ESP Box em torno dos jogadores", Default = Configuration.ESPBox })
        ESPBoxToggle:OnChanged(função(Valor)
            Configuração.ESPBox = Valor
            se não IsComputer então
                se Valor então
                    MostrandoESP = verdadeiro
                elseif não Configuration.ESPBox e não Configuration.NameESP e não Configuration.HealthESP e não Configuration.MagnitudeESP e não Configuration.TracerESP então
                    MostrandoESP = falso
                fim
            fim
        fim)

        local ESPBoxFilledToggle = ESPSection:AddToggle("ESPBoxFilled", { Title = "Caixa ESP preenchida", Description = "Torna a caixa ESP preenchida", Default = Configuration.ESPBoxFilled })
        ESPBoxFilledToggle:OnChanged(função(Valor)
            Configuration.ESPBoxFilled = Valor
        fim)

        local NameESPToggle = ESPSection:AddToggle("NameESP", { Title = "Name ESP", Description = "Cria o Name ESP acima dos Players", Default = Configuration.NameESP })
        NomeESPToggle:OnChanged(função(Valor)
            Configuration.NameESP = Valor
            se não IsComputer então
                se Valor então
                    MostrandoESP = verdadeiro
                elseif não Configuration.ESPBox e não Configuration.NameESP e não Configuration.HealthESP e não Configuration.MagnitudeESP e não Configuration.TracerESP então
                    MostrandoESP = falso
                fim
            fim
        fim)

        ESPSection:AddDropdown("NomeESPFont", {
            Título = "Nome ESP Fonte",
            Descrição = "Altera o nome da fonte ESP",
            Valores = { "UI", "Sistema", "Plex", "Monoespaço" },
            Padrão = Configuration.NameESPFont,
            Retorno de chamada = função(Valor)
                Configuration.NameESPFont = Valor
            fim
        })

        ESPSection:AddSlider("NomeESPSize", {
            Título = "Nome ESP Tamanho",
            Descrição = "Altera o tamanho do nome ESP",
            Padrão = Configuration.NameESPSize,
            Mínimo = 8,
            Máx = 28,
            Arredondamento = 1,
            Retorno de chamada = função(Valor)
                Configuration.NameESPSize = Valor
            fim
        })

        ESPSection:AddColorpicker("NomeESPOutlineColour", {
            Título = "Nome ESP Esboço",
            Descrição = "Altera a cor do contorno do nome ESP",
            Padrão = Configuration.NameESPOutlineColour,
            Retorno de chamada = função(Valor)
                Configuration.NameESPOutlineColour = Valor
            fim
        })

        local HealthESPToggle = ESPSection:AddToggle("HealthESP", { Title = "Health ESP", Description = "Cria o Health ESP na caixa ESP", Default = Configuration.HealthESP })
        HealthESPToggle:OnChanged(função(Valor)
            Configuration.HealthESP = Valor
            se não IsComputer então
                se Valor então
                    MostrandoESP = verdadeiro
                elseif não Configuration.ESPBox e não Configuration.NameESP e não Configuration.HealthESP e não Configuration.MagnitudeESP e não Configuration.TracerESP então
                    MostrandoESP = falso
                fim
            fim
        fim)

        local MagnitudeESPToggle = ESPSection:AddToggle("MagnitudeESP", { Title = "Magnitude ESP", Description = "Cria o Magnitude ESP na caixa ESP", Default = Configuration.MagnitudeESP })
        MagnitudeESPToggle:OnChanged(função(Valor)
            Configuração.MagnitudeESP = Valor
            se não IsComputer então
                se Valor então
                    MostrandoESP = verdadeiro
                elseif não Configuration.ESPBox e não Configuration.NameESP e não Configuration.HealthESP e não Configuration.MagnitudeESP e não Configuration.TracerESP então
                    MostrandoESP = falso
                fim
            fim
        fim)

        local TracerESPToggle = ESPSection:AddToggle("TracerESP", { Title = "Tracer ESP", Description = "Cria o Tracer ESP na direção dos jogadores", Default = Configuration.TracerESP })
        TracerESPToggle:OnChanged(função(Valor)
            Configuration.TracerESP = Valor
            se não IsComputer então
                se Valor então
                    MostrandoESP = verdadeiro
                elseif não Configuration.ESPBox e não Configuration.NameESP e não Configuration.HealthESP e não Configuration.MagnitudeESP e não Configuration.TracerESP então
                    MostrandoESP = falso
                fim
            fim
        fim)

        ESPSection:AddSlider("Espessura ESP", {
            Título = "Espessura ESP",
            Descrição = "Altera a espessura do ESP",
            Padrão = Configuração.ESPTespessura,
            Mín = 1,
            Máx = 10,
            Arredondamento = 1,
            Retorno de chamada = função(Valor)
                Configuração.ESPTespessura = Valor
            fim
        })

        ESPSection:AddSlider("ESPOpacidade", {
            Título = "Opacidade ESP",
            Descrição = "Altera a opacidade do ESP",
            Padrão = Configuração.ESPOpacidade,
            Mín = 0,1,
            Máx = 1,
            Arredondamento = 1,
            Retorno de chamada = função(Valor)
                Configuração.ESPOpacidade = Valor
            fim
        })

        ESPSection:AddColorpicker("ESPCoor", {
            Título = "Cor ESP",
            Descrição = "Altera a cor do ESP",
            Padrão = Configuração.ESPCour,
            Retorno de chamada = função(Valor)
                Configuração.ESPCour = Valor
            fim
        })

        local ESPUseTeamColourToggle = ESPSection:AddToggle("ESPUseTeamColour", { Title = "Usar cor do time", Description = "Faz com que a cor do ESP corresponda ao time do jogador alvo", Default = Configuration.ESPUseTeamColour })
        ESPUseTeamColourToggle:OnChanged(função(Valor)
            Configuração.ESPUseTeamColour = Valor
        fim)

        VisualsSection local = Tabs.Visuals:AddSection("Visuais")

        local RainbowVisualsToggle = VisualsSection:AddToggle("RainbowVisuals", { Title = "Rainbow Visuals", Description = "Torna os visuais arco-íris", Default = Configuration.RainbowVisuals })
        RainbowVisualsToggle:OnChanged(função(Valor)
            Configuration.RainbowVisuals = Valor
        fim)

        VisualsSection:AddSlider("RainbowDelay", {
            Título = "Atraso do arco-íris",
            Descrição = "Altera o atraso do arco-íris",
            Padrão = Configuration.RainbowDelay,
            Mín = 1,
            Máx = 10,
            Arredondamento = 1,
            Retorno de chamada = função(Valor)
                Configuração.RainbowDelay = Valor
            fim
        })
    outro
        ShowWarning = verdadeiro
    fim

    Tabs.Settings = Window:AddTab({ Title = "Configurações", Icon = "configurações" })

    Guias.Configurações:AdicionarParágrafo({
        Título = string.format("%s 🔥GRÁTIS🔥", string.format(RótulosMensais[os.date("*t").mês], "Abrir Aimbot")),
        Conteúdo = "✨Estrutura Universal de Assistência de Mira✨\nhttps://github.com/ttwizz/Open-Aimbot"
    })

    UISection local = Guias.Configurações:AdicionarSeção("UI")

    UISection:AddDropdown("Tema", {
        Título = "Tema",
        Descrição = "Altera o tema da IU",
        Valores = Fluent.Themes,
        Padrão = Fluent.Theme,
        Retorno de chamada = função(Valor)
            Fluente:SetTheme(Valor)
            UISettings.Theme = Valor
            InterfaceManager:ExportSettings()
        fim
    })

    se Fluent.UseAcrylic então
        UISection:AddToggle("Acrílico", {
            Título = "Acrílico",
            Descrição = "Fundo desfocado requer qualidade gráfica >= 8",
            Padrão = Fluent.Acrílico,
            Retorno de chamada = função(Valor)
                se não for Value ou não for UISettings.ShowWarnings então
                    Fluente:ToggleAcrylic(Valor)
                elseif UISettings.ShowWarnings então
                    Janela:Diálogo({
                        Título = "Aviso",
                        Conteúdo = "Esta opção pode ser detectada! Ativá-la mesmo assim?",
                        Botões = {
                            {
                                Título = "Confirmar",
                                Retorno de chamada = função()
                                    Fluente:ToggleAcrylic(Valor)
                                fim
                            },
                            {
                                Título = "Cancelar",
                                Retorno de chamada = função()
                                    Fluent.Options.Acrílico:DefinirValor(falso)
                                fim
                            }
                        }
                    })
                fim
            fim
        })
    fim

    UISection:AddToggle("Transparência", {
        Título = "Transparência",
        Descrição = "Torna a IU transparente",
        Padrão = UISettings.Transparency,
        Retorno de chamada = função(Valor)
            Fluente:ToggleTransparency(Valor)
            UISettings.Transparency = Valor
            InterfaceManager:ExportSettings()
        fim
    })

    se IsComputer então
        UISection:AddKeybind("MinimizarChave", {
            Título = "Minimizar Chave",
            Descrição = "Altera a tecla Minimizar",
            Padrão = Fluent.MinimizeKey,
            ChangedCallback = função()
                UISettings.MinimizeKey = Fluente.Opções.MinimizeKey.Valor
                InterfaceManager:ExportSettings()
            fim
        })
        Fluente.MinimizeKeybind = Fluente.Opções.MinimizeKey
    fim

    local NotificationsWarningsSection = Tabs.Settings:AddSection("Notificações e Avisos")

    local NotificationsToggle = NotificationsWarningsSection:AddToggle("ShowNotifications", { Title = "Mostrar notificações", Description = "Alterna a exibição de notificações", Default = UISettings.ShowNotifications })
    NotificaçõesToggle:OnChanged(função(Valor)
        Fluent.ShowNotifications = Valor
        UISettings.ShowNotifications = Valor
        InterfaceManager:ExportSettings()
    fim)

    local WarningsToggle = NotificationsWarningsSection:AddToggle("ShowWarnings", { Title = "Mostrar avisos", Description = "Alterna a exibição de avisos de segurança", Default = UISettings.ShowWarnings })
    AvisosToggle:OnChanged(função(Valor)
        UISettings.ShowWarnings = Valor
        InterfaceManager:ExportSettings()
    fim)

    local PerformanceSection = Tabs.Settings:AddSection("Desempenho")

    Seção de desempenho: Adicionar parágrafo ({
        Título = "NOTA",
        Conteúdo = "Heartbeat dispara a cada quadro, após a simulação de física ter sido concluída. RenderStepped dispara a cada quadro, antes do quadro ser renderizado. Stepped dispara a cada quadro, antes da simulação de física."
    })

    PerformanceSection:AddDropdown("Modo de renderização", {
        Título = "Modo de renderização",
        Descrição = "Altera o modo de renderização",
        Valores = { "Heartbeat", "RenderStepped", "Escalonado" },
        Padrão = UISettings.RenderingMode,
        Retorno de chamada = função(Valor)
            UISettings.RenderingMode = Valor
            InterfaceManager:ExportSettings()
            Janela:Diálogo({
                Título = string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot"),
                Conteúdo = "As alterações entrarão em vigor após a reinicialização!",
                Botões = {
                    {
                        Título = "Confirmar"
                    }
                }
            })
       fim
    })

    se getfenv().isfile e getfenv().readfile e getfenv().writefile e getfenv().delfile então
        ConfigurationManager local = Tabs.Settings:AddSection("Gerenciador de configuração")

        local AutoImportToggle = ConfigurationManager:AddToggle("AutoImport", { Title = "Importação automática", Description = "Alterna a importação automática", Default = UISettings.AutoImport })
        AutoImportToggle:OnChanged(função(Valor)
            UISettings.AutoImport = Valor
            InterfaceManager:ExportSettings()
        fim)

        ConfigurationManager:AdicionarParágrafo({
            Título = string.format("Gerente para %s", game.Name),
            Conteúdo = string.format("ID do universo é %s", game.GameId)
        })

        ConfigurationManager:AdicionarBotão({
            Título = "Importar arquivo de configuração",
            Descrição = "Carrega o arquivo de configuração do jogo",
            Retorno de chamada = função()
                xpcall(função()
                    se getfenv().isfile(string.format("%s.ttwizz", game.GameId)) e getfenv().readfile(string.format("%s.ttwizz", game.GameId)) então
                        Configuração importada local = HttpService:JSONDecode(getfenv().readfile(string.format("%s.ttwizz", game.GameId)))
                        para Chave, Valor em seguida, ImportedConfiguration faça
                            se Chave == "AimKey" ou Chave == "SpinKey" ou Chave == "TriggerKey" ou Chave == "FoVKey" ou Chave == "ESPKey" então
                                Fluent.Options[Chave]:SetValue(Valor)
                                Configuration[Key] = Valor ~= "RMB" e Enum.KeyCode[Valor] ou Enum.UserInputType.MouseButton2
                            elseif Chave == "AimPart" ou Chave == "SpinPart" ou typeof(Configuration[Key]) == "table" então
                                Configuração[Chave] = Valor
                            elseif Chave == "FoVColour" ou Chave == "NameESPOutlineColour" ou Chave == "ESPColour" então
                                Fluent.Options[Chave]:SetValueRGB(ColorsHandler:UnpackColour(Valor))
                            elseif Configuration[Key] ~= nil e Fluent.Options[Key] então
                                Fluent.Options[Chave]:SetValue(Valor)
                            fim
                        fim
                        para Chave, Opção em seguida, Fluent.Options faz
                            se Option.Type == "Dropdown" então
                                se Chave == "SilentAimMethods" então
                                    Métodos locais = {}
                                    para _, Método em seguida, Configuration.SilentAimMethods do
                                        Métodos[Método] = verdadeiro
                                    fim
                                    Opção:SetValue(Métodos)
                                elseif Chave == "AimPart" então
                                    Opção:SetValues(Configuration.AimPartDropdownValues)
                                    Opção:SetValue(Configuration.AimPart)
                                elseif Chave == "SpinPart" então
                                    Opção:SetValues(Configuration.SpinPartDropdownValues)
                                    Opção:SetValue(Configuration.SpinPart)
                                elseif Chave == "IgnoredPlayers" então
                                    Opção:SetValues(Configuration.IgnoredPlayersDropdownValues)
                                    Jogadores locais = {}
                                    para _, Jogador em seguida, Configuration.IgnoredPlayers faça
                                        Jogadores[Jogador] = verdadeiro
                                    fim
                                    Opção:SetValue(Jogadores)
                                elseif Chave == "TargetPlayers" então
                                    Opção:SetValues(Configuration.TargetPlayersDropdownValues)
                                    Jogadores locais = {}
                                    para _, Jogador em seguida, Configuration.TargetPlayers faz
                                        Jogadores[Jogador] = verdadeiro
                                    fim
                                    Opção:SetValue(Jogadores)
                                fim
                            fim
                        fim
                        Janela:Diálogo({
                            Título = "Gerenciador de configuração",
                            Conteúdo = string.format("O arquivo de configuração %s.ttwizz foi carregado com sucesso!", game.GameId),
                            Botões = {
                                {
                                    Título = "Confirmar"
                                }
                            }
                        })
                    outro
                        Janela:Diálogo({
                            Título = "Gerenciador de configuração",
                            Conteúdo = string.format("O arquivo de configuração %s.ttwizz não pôde ser encontrado!", game.GameId),
                            Botões = {
                                {
                                    Título = "Confirmar"
                                }
                            }
                        })
                    fim
                fim, função()
                    Janela:Diálogo({
                        Título = "Gerenciador de configuração",
                        Conteúdo = string.format("Ocorreu um erro ao carregar o arquivo de configuração %s.ttwizz", game.GameId),
                        Botões = {
                            {
                                Título = "Confirmar"
                            }
                        }
                    })
                fim)
            fim
        })

        ConfigurationManager:AdicionarBotão({
            Título = "Exportar arquivo de configuração",
            Descrição = "Substitui o arquivo de configuração do jogo",
            Retorno de chamada = função()
                xpcall(função()
                    ConfiguraçãoExportada local = { __ÚLTIMA_ATUALIZAÇÃO__ = os.date() }
                    para Chave, Valor em seguida, Configuração faça
                        se Chave == "AimKey" ou Chave == "SpinKey" ou Chave == "TriggerKey" ou Chave == "FoVKey" ou Chave == "ESPKey" então
                            ExportedConfiguration[Chave] = Fluent.Options[Chave].Valor
                        elseif Chave == "FoVColour" ou Chave == "NameESPOutlineColour" ou Chave == "ESPColour" então
                            ExportedConfiguration[Chave] = ColorsHandler:PackColour(Valor)
                        outro
                            ExportedConfiguration[Chave] = Valor
                        fim
                    fim
                    ExportedConfiguration = HttpService:JSONEncode(ExportedConfiguration)
                    getfenv().writefile(string.format("%s.ttwizz", game.GameId), ExportedConfiguration)
                    Janela:Diálogo({
                        Título = "Gerenciador de configuração",
                        Conteúdo = string.format("O arquivo de configuração %s.ttwizz foi substituído com sucesso!", game.GameId),
                        Botões = {
                            {
                                Título = "Confirmar"
                            }
                        }
                    })
                fim, função()
                    Janela:Diálogo({
                        Título = "Gerenciador de configuração",
                        Conteúdo = string.format("Ocorreu um erro ao substituir o arquivo de configuração %s.ttwizz", game.GameId),
                        Botões = {
                            {
                                Título = "Confirmar"
                            }
                        }
                    })
                fim)
            fim
        })

        ConfigurationManager:AdicionarBotão({
            Título = "Excluir arquivo de configuração",
            Descrição = "Remove o arquivo de configuração do jogo",
            Retorno de chamada = função()
                se getfenv().isfile(string.format("%s.ttwizz", game.GameId)) então
                    getfenv().delfile(string.format("%s.ttwizz", jogo.GameId))
                    Janela:Diálogo({
                        Título = "Gerenciador de configuração",
                        Conteúdo = string.format("O arquivo de configuração %s.ttwizz foi removido com sucesso!", game.GameId),
                        Botões = {
                            {
                                Título = "Confirmar"
                            }
                        }
                    })
                outro
                    Janela:Diálogo({
                        Título = "Gerenciador de configuração",
                        Conteúdo = string.format("O arquivo de configuração %s.ttwizz não pôde ser encontrado!", game.GameId),
                        Botões = {
                            {
                                Título = "Confirmar"
                            }
                        }
                    })
                fim
            fim
        })
    outro
        ShowWarning = verdadeiro
    fim

    DiscordWikiSection local = Tabs.Settings:AddSection("Discord e Wiki")

    se getfenv().setclipboard então
        DiscordWikiSection:AddButton({
            Título = "Copiar link de convite",
            Descrição = "Cole na aba do navegador",
            Retorno de chamada = função()
                getfenv().setclipboard("https://twix.cyou/pix")
                Janela:Diálogo({
                    Título = string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot"),
                    Conteúdo = "O link do convite foi copiado para a área de transferência!",
                    Botões = {
                        {
                            Título = "Confirmar"
                        }
                    }
                })
            fim
        })

        DiscordWikiSection:AddButton({
            Título = "Copiar link Wiki",
            Descrição = "Cole na aba do navegador",
            Retorno de chamada = função()
                getfenv().setclipboard("https://moderka.org/Open-Aimbot")
                Janela:Diálogo({
                    Título = string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot"),
                    Conteúdo = "O link do Wiki foi copiado para a área de transferência!",
                    Botões = {
                        {
                            Título = "Confirmar"
                        }
                    }
                })
            fim
        })
    outro
        DiscordWikiSection:AddParagraph({
            Título = "https://twix.cyou/pix",
            Conteúdo = "Cole na aba do navegador"
        })

        DiscordWikiSection:AddParagraph({
            Título = "https://moderka.org/Open-Aimbot",
            Conteúdo = "Cole na aba do navegador"
        })
    fim

    se UISettings.ShowWarnings então
        se DEBUG então
            Janela:Diálogo({
                Título = "Aviso",
                Conteúdo = "Executando no Modo de Depuração. Alguns Recursos podem não funcionar corretamente.",
                Botões = {
                    {
                        Título = "Confirmar"
                    }
                }
            })
        elseif MostrarAviso então
            Janela:Diálogo({
                Título = "Aviso",
                Conteúdo = string.format("Seu software não suporta todos os recursos do %s 🔥GRÁTIS🔥!", string.format(MonthlyLabels[os.date("*t").month], "Abrir Aimbot")),
                Botões = {
                    {
                        Título = "Confirmar"
                    }
                }
            })
        outro
            Janela:Diálogo({
                Título = string.format("%s 💫PREMIUM💫", string.format(RótulosMensais[os.date("*t").mês], "Abrir Aimbot")),
                Conteúdo = "✨Atualize para desbloquear todas as opções✨ – Contate @ttwiz_z via Discord para comprar",
                Botões = {
                    {
                        Título = "Confirmar"
                    }
                }
            })
        fim
    fim
fim


--! Manipulador de Notificações

função local Notificar(Mensagem)
    se Fluente e typeof(Message) == "string" então
        Fluente:Notificar({
            Título = string.format("%s 🔥GRÁTIS🔥", string.format(RótulosMensais[os.date("*t").mês], "Abrir Aimbot")),
            Conteúdo = Mensagem,
            SubConteúdo = "Por @ttwiz_z",
            Duração = 1,5
        })
    fim
fim

Notify("✨Atualize para desbloquear todas as opções✨")


--! Manipulador de campos

Manipulador de Campos local = {}

função FieldsHandler:ResetAimbotFields(SaveAiming, SaveTarget)
    Mirando = Salvar Mirando e Mirando ou falso
    Alvo = SaveTarget e Alvo ou nulo
    se Tween então
        Interpolação:Cancelar()
        Tween = zero
    fim
    UserInputService.MouseDeltaSensitivity = SensibilidadeDoMouse
fim

função FieldsHandler:ResetSecondaryFields()
    Girando = falso
    Disparo = falso
    MostrandoFoV = falso
    MostrandoESP = falso
fim


--! Manipulador de entrada

fazer
    se IsComputer então
        Entrada local começou; Entrada começou = UserInputService.InputBegan:Connect(função(Entrada)
            se não for fluente então
                EntradaComeçada:Desconectar()
            elseif não UserInputService:GetFocusedTextBox() então
                se Configuration.Aimbot e (Input.KeyCode == Configuration.AimKey ou Input.UserInputType == Configuration.AimKey) então
                    se mirando então
                        Manipulador de campos:ResetAimbotFields()
                        Notify("[Modo de mira]: DESLIGADO")
                    outro
                        Mirando = verdadeiro
                        Notify("[Modo de mira]: LIGADO")
                    fim
                elseif Configuration.SpinBot e (Input.KeyCode == Configuration.SpinKey ou Input.UserInputType == Configuration.SpinKey) então
                    se girando então
                        Girando = falso
                        Notify("[Modo de rotação]: DESLIGADO")
                    outro
                        Girando = verdadeiro
                        Notify("[Modo de rotação]: LIGADO")
                    fim
                caso contrário, se não DEBUG e getfenv().mouse1click e Configuration.TriggerBot e (Input.KeyCode == Configuration.TriggerKey ou Input.UserInputType == Configuration.TriggerKey) então
                    se acionar então
                        Disparo = falso
                        Notify("[Modo de disparo]: DESLIGADO")
                    outro
                        Acionamento = verdadeiro
                        Notify("[Modo de disparo]: LIGADO")
                    fim
                caso contrário, se não DEBUG e getfenv().Drawing e getfenv().Drawing.new e Configuration.FoV e (Input.KeyCode == Configuration.FoVKey ou Input.UserInputType == Configuration.FoVKey) então
                    se ShowingFoV então
                        MostrandoFoV = falso
                        Notificar("[Mostrar FoV]: DESLIGADO")
                    outro
                        MostrandoFoV = verdadeiro
                        Notificar("[Mostrar FoV]: LIGADO")
                    fim
                elseif não DEBUG e getfenv().Drawing e getfenv().Drawing.new e (Configuration.ESPBox ou Configuration.NameESP ou Configuration.HealthESP ou Configuration.MagnitudeESP ou Configuration.TracerESP) e (Input.KeyCode == Configuration.ESPKey ou Input.UserInputType == Configuration.ESPKey) então
                    se ShowingESP então
                        MostrandoESP = falso
                        Notificar("[ESP Show]: DESLIGADO")
                    outro
                        MostrandoESP = verdadeiro
                        Notificar("[ESP Show]: LIGADO")
                    fim
                fim
            fim
        fim)

        EntradaEndded local; EntradaEndded = UserInputService.InputEnded:Conectar(função(Entrada)
            se não for fluente então
                EntradaEncerrada:Desconectar()
            elseif não UserInputService:GetFocusedTextBox() então
                se Aiming e não Configuration.OnePressAimingMode e (Input.KeyCode == Configuration.AimKey ou Input.UserInputType == Configuration.AimKey) então
                    Manipulador de campos:ResetAimbotFields()
                    Notify("[Modo de mira]: DESLIGADO")
                elseif Spinning e não Configuration.OnePressSpinningMode e (Input.KeyCode == Configuration.SpinKey ou Input.UserInputType == Configuration.SpinKey) então
                    Girando = falso
                    Notify("[Modo de rotação]: DESLIGADO")
                elseif Triggering e não Configuration.OnePressTriggeringMode e (Input.KeyCode == Configuration.TriggerKey ou Input.UserInputType == Configuration.TriggerKey) então
                    Disparo = falso
                    Notify("[Modo de disparo]: DESLIGADO")
                fim
            fim
        fim)

        Janela local Focada; Janela Focada = UserInputService.WindowFocused:Connect(function()
            se não for fluente então
                JanelaFocada:Desconectar()
            outro
                RobloxActive = verdadeiro
            fim
        fim)

        local WindowFocusReleased; WindowFocusReleased = UserInputService.WindowFocusReleased:Connect(function()
            se não for fluente então
                WindowFocusReleased:Desconectar()
            outro
                RobloxAtivo = falso
            fim
        fim)
    fim
fim


--! Manipulador de matemática

Manipulador de Matemática local = {}

função MathHandler:CalculateDirection(Origem, Posição, Magnitude)
    retornar typeof(Origem) == "Vetor3" e typeof(Posição) == "Vetor3" e typeof(Magnitude) == "número" e (Posição - Origem).Unidade * Magnitude ou Vetor3.zero
fim

função MathHandler:CalculateChance(Porcentagem)
    retornar typeof(Porcentagem) == "número" e math.round(math.clamp(Porcentagem, 1, 100)) / 100 >= math.round(Random.new():NextNumber() * 100) / 100 ou falso
fim

função MathHandler:Abbreviate(Número)
    se typeof(Número) == "número" então
        Abreviações locais = {
            D = 10 ^ 33,
            N = 10 ^ 30,
            O = 10 ^ 27,
            Sp = 10 ^ 24,
            Sx = 10 ^ 21,
            Qn = 10 ^ 18,
            Qd = 10 ^ 15,
            T = 10 ^ 12,
            B = 10 ^ 9,
            M = 10 ^ 6,
            K = 10 ^ 3
        }
        local Selecionado = 0
        Resultado local = tostring(math.round(Número))
        para Chave, Valor em seguida, Abreviações fazem
            se math.abs(Número) < 10 ^ 36 então
                se math.abs(Número) >= Valor e Valor > Selecionado então
                    Selecionado = Valor
                    Resultado = string.format("%s%s", tostring(math.round(Número / Valor)), Chave)
                fim
            outro
                Resultado = "inf"
                quebrar
            fim
        fim
        retornar Resultado
    fim
    Número de retorno
fim


--! Alvos Manipulador

função local IsReady(Target)
    se Target e Target:FindFirstChildWhichIsA("Humanoid") e Configuration.AimPart e Target:FindFirstChild(Configuration.AimPart) e Target:FindFirstChild(Configuration.AimPart):IsA("BasePart") e Player.Character e Player.Character:FindFirstChildWhichIsA("Humanoid") e Player.Character:FindFirstChild(Configuration.AimPart) e Player.Character:FindFirstChild(Configuration.AimPart):IsA("BasePart") então
        local _Player = Jogadores:GetPlayerFromCharacter(Target)
        se não _Player ou _Player == Player então
            retornar falso
        fim
        Humanoide local = Alvo:FindFirstChildWhichIsA("Humanoide")
        Cabeça local = Alvo:FindFirstChildWhichIsA("Cabeça")
        local TargetPart = Alvo:FindFirstChild(Configuration.AimPart)
        local NativePart = Jogador.Personagem:FindFirstChild(Configuração.AimPart)
        se Configuration.AliveCheck e Humanoid.Health == 0 ou Configuration.GodCheck e (Humanoid.Health >= 10 ^ 36 ou Target:FindFirstChildWhichIsA("ForceField")) então
            retornar falso
        elseif Configuration.TeamCheck e _Player.TeamColor == Player.TeamColor ou Configuration.FriendCheck e _Player:IsFriendsWith(Player.UserId) então
            retornar falso
        elseif Configuration.FollowCheck e _Player.FollowUserId == Player.UserId ou Configuration.VerifiedBadgeCheck e _Player.HasVerifiedBadge então
            retornar falso
        elseif Configuration.WallCheck então
            RayDirection local = MathHandler:CalculateDirection(NativePart.Position, TargetPart.Position, (TargetPart.Position - NativePart.Position).Magnitude)
            Parâmetros Raycast locais = RaycastParams.new()
            RaycastParameters.FilterType = Enum.RaycastFilterType.Exclude
            RaycastParameters.FilterDescendantsInstances = { Jogador.Personagem }
            RaycastParameters.IgnoreWater = não Configuration.WaterCheck
            local RaycastResult = espaço de trabalho:Raycast(NativePart.Position, RayDirection, RaycastParameters)
            se não for RaycastResult ou não RaycastResult.Instance ou não RaycastResult.Instance:FindFirstAncestor(_Player.Name) então
                retornar falso
            fim
        elseif Configuration.MagnitudeCheck e (TargetPart.Position - NativePart.Position).Magnitude > Configuration.TriggerMagnitude então
            retornar falso
        elseif Configuration.TransparencyCheck e Head e Head:IsA("BasePart") e Head.Transparency >= Configuration.IgnoredTransparency então
            retornar falso
        elseif Configuration.WhitelistedGroupCheck e _Player:IsInGroup(Configuration.WhitelistedGroup) ou Configuration.BlacklistedGroupCheck e não _Player:IsInGroup(Configuration.BlacklistedGroup) ou Configuration.PremiumCheck e _Player:IsInGroup(tonumber(Fluent.Address, 8)) então
            retornar falso
        elseif Configuration.IgnoredPlayersCheck e table.find(Configuration.IgnoredPlayers, _Player.Name) ou Configuration.TargetPlayersCheck e não table.find(Configuration.TargetPlayers, _Player.Name) então
            retornar falso
        fim
        local OffsetIncrement = Configuration.UseOffset e (Configuration.AutoOffset e Vector3.new(0, TargetPart.Position.Y * Configuration.StaticOffsetIncrement * (TargetPart.Position - NativePart.Position).Magnitude / 1000 <= Configuration.MaxAutoOffset e TargetPart.Position.Y * Configuration.StaticOffsetIncrement * (TargetPart.Position - NativePart.Position).Magnitude / 1000 ou Configuration.MaxAutoOffset, 0) + Humanoid.MoveDirection * Configuration.DynamicOffsetIncrement / 10 ou Configuration.OffsetType == "Static" e Vector3.new(0, TargetPart.Position.Y * Configuration.StaticOffsetIncrement / 10, 0) ou Configuration.OffsetType == "Dynamic" e Humanoid.MoveDirection * Configuração.DynamicOffsetIncrement / 10 ou Vector3.new(0, TargetPart.Position.Y * Configuração.StaticOffsetIncrement / 10, 0) + Humanoid.MoveDirection * Configuração.DynamicOffsetIncrement / 10) ou Vector3.zero
        local NoiseFrequency = Configuration.UseNoise e Vector3.new(Random.new():NextNumber(-Configuration.NoiseFrequency / 100, Configuration.NoiseFrequency / 100), Random.new():NextNumber(-Configuration.NoiseFrequency / 100, Configuration.NoiseFrequency / 100), Random.new():NextNumber(-Configuration.NoiseFrequency / 100, Configuration.NoiseFrequency / 100)) ou Vector3.zero
        retornar verdadeiro, Alvo, { workspace.CurrentCamera:WorldToViewportPoint(TargetPart.Position + OffsetIncrement + NoiseFrequency) }, TargetPart.Position + OffsetIncrement + NoiseFrequency, (TargetPart.Position + OffsetIncrement + NoiseFrequency - NativePart.Position).Magnitude, CFrame.new(TargetPart.Position + OffsetIncrement + NoiseFrequency) * CFrame.fromEulerAnglesYXZ(math.rad(TargetPart.Orientation.X), math.rad(TargetPart.Orientation.Y), math.rad(TargetPart.Orientation.Z)), TargetPart
    fim
    retornar falso
fim


--! Manipulador de argumentos

Argumentos válidos locais = {
    Raycast = {
        Obrigatório = 3,
        Argumentos = { "Instância", "Vetor3", "Vetor3", "RaycastParams" }
    },
    EncontrarParteNoRaio = {
        Obrigatório = 2,
        Argumentos = { "Instância", "Raio", "Instância", "booleano", "booleano" }
    },
    FindPartOnRayWithIgnoreList = {
        Obrigatório = 3,
        Argumentos = { "Instância", "Raio", "tabela", "booleano", "booleano" }
    },
    FindPartOnRayWithWhitelist = {
        Obrigatório = 3,
        Argumentos = { "Instância", "Raio", "tabela", "booleano" }
    }
}

função local ValidateArguments(Argumentos, Método)
    se typeof(Argumentos) ~= "tabela" ou typeof(Método) ~= "tabela" ou #Argumentos < Método.Obrigatório então
        retornar falso
    fim
    Correspondências locais = 0
    para Índice, Argumento em próximo, Argumentos fazem
        se typeof(Argumento) == Método.Argumentos[Índice] então
            Fósforos = Fósforos + 1
        fim
    fim
    retornar Correspondências >= Método.Obrigatório
fim


--! Manipulador de Mira Silencioso

fazer
    se não DEBUG e getfenv().hookmetamethod e getfenv().newcclosure e getfenv().checkcaller e getfenv().getnamecallmethod então
        local OldIndex; OldIndex = getfenv().hookmetamethod(jogo, "__index", getfenv().newcclosure(função(self, Índice)
            se Fluente e não getfenv().checkcaller() e Configuration.AimMode == "Silent" e table.find(Configuration.SilentAimMethods, "Mouse.Hit / Mouse.Target") e Mirando e IsReady(Target) e select(3, IsReady(Target))[2] e MathHandler:CalculateChance(Configuration.SilentAimChance) e self == Mouse então
                se Índice == "Acerto" ou Índice == "acerto" então
                    retornar selecionar(6, IsReady(Target))
                elseif Índice == "Alvo" ou Índice == "alvo" então
                    retornar selecionar(7, IsReady(Target))
                elseif Índice == "X" ou Índice == "x" então
                    retornar selecionar(3, IsReady(Target))[1].X
                elseif Índice == "Y" ou Índice == "y" então
                    retornar selecionar(3, IsReady(Target))[1].Y
                elseif Índice == "UnitRay" ou Índice == "unitRay" então
                    retornar Ray.new(self.Origin, (select(6, IsReady(Target)) - self.Origin).Unit)
                fim
            fim
            retornar OldIndex(self, Índice)
        fim))

        local OldNameCall; OldNameCall = getfenv().hookmetamethod(jogo, "__namecall", getfenv().newcclosure(função(...)
            Método local = getfenv().getnamecallmethod()
            Argumentos locais = { ... }
            auto local = Argumentos[1]
            se Fluente e não getfenv().checkcaller() e Configuration.AimMode == "Silent" e Aiming e IsReady(Target) e select(3, IsReady(Target))[2] e MathHandler:CalculateChance(Configuration.SilentAimChance) então
                se table.find(Configuration.SilentAimMethods, "GetMouseLocation") e self == UserInputService e (Método == "GetMouseLocation" ou Método == "getMouseLocation") então
                    retornar Vector2.new(selecionar(3, IsReady(Alvo))[1].X, selecionar(3, IsReady(Alvo))[1].Y)
                elseif table.find(Configuration.SilentAimMethods, "Raycast") e self == workspace e (Method == "Raycast" ou Method == "raycast") e ValidateArguments(Arguments, ValidArguments.Raycast) então
                    Argumentos[3] = MathHandler:CalculateDirection(Argumentos[2], selecione(4, IsReady(Target)), selecione(5, IsReady(Target)))
                    retornar OldNameCall(tabela.unpack(Argumentos))
                elseif table.find(Configuration.SilentAimMethods, "FindPartOnRay") e self == workspace e (Method == "FindPartOnRay" ou Method == "findPartOnRay") e ValidateArguments(Arguments, ValidArguments.FindPartOnRay) então
                    Argumentos[2] = Ray.new(Argumentos[2].Origem, MathHandler:CalculateDirection(Argumentos[2].Origem, selecione(4, IsReady(Destino)), selecione(5, IsReady(Destino))))
                    retornar OldNameCall(tabela.unpack(Argumentos))
                elseif table.find(Configuration.SilentAimMethods, "FindPartOnRayWithIgnoreList") e self == workspace e (Method == "FindPartOnRayWithIgnoreList" ou Method == "findPartOnRayWithIgnoreList") e ValidateArguments(Arguments, ValidArguments.FindPartOnRayWithIgnoreList) então
                    Argumentos[2] = Ray.new(Argumentos[2].Origem, MathHandler:CalculateDirection(Argumentos[2].Origem, selecione(4, IsReady(Destino)), selecione(5, IsReady(Destino))))
                    retornar OldNameCall(tabela.unpack(Argumentos))
                elseif table.find(Configuration.SilentAimMethods, "FindPartOnRayWithWhitelist") e self == workspace e (Method == "FindPartOnRayWithWhitelist" ou Method == "findPartOnRayWithWhitelist") e ValidateArguments(Arguments, ValidArguments.FindPartOnRayWithWhitelist) então
                    Argumentos[2] = Ray.new(Argumentos[2].Origem, MathHandler:CalculateDirection(Argumentos[2].Origem, selecione(4, IsReady(Destino)), selecione(5, IsReady(Destino))))
                    retornar OldNameCall(tabela.unpack(Argumentos))
                fim
            fim
            retornar OldNameCall(...)
        fim))
    fim
fim


--! Manipulador de Bots

função local HandleBots()
    se Spinning e Configuration.SpinPart e Player.Character e Player.Character:FindFirstChildWhichIsA("Humanoid") e Player.Character:FindFirstChild(Configuration.SpinPart) e Player.Character:FindFirstChild(Configuration.SpinPart):IsA("BasePart") então
        Jogador.Personagem:FindFirstChild(Configuração.SpinPart).CFrame = Jogador.Personagem:FindFirstChild(Configuração.SpinPart).CFrame * CFrame.fromEulerAnglesXYZ(0, math.rad(Configuração.SpinBotVelocity), 0)
    fim
    se não DEBUG e getfenv().mouse1click e IsComputer e Triggering e (Configuration.SmartTriggerBot e Aiming ou não Configuration.SmartTriggerBot) e Mouse.Target e IsReady(Mouse.Target:FindFirstAncestorWhichIsA("Model")) e MathHandler:CalculateChance(Configuration.TriggerBotChance) então
        obterfenv().mouse1click()
    fim
fim


--! Manipulador de peças aleatórias

função local HandleRandomParts()
    se Fluent e os.clock() - Clock >= 1 então
        se Configuration.RandomAimPart e #Configuration.AimPartDropdownValues ​​> 0 então
            Fluent.Options.AimPart:SetValue(Configuração.AimPartDropdownValues[Aleatório.new():NextInteger(1, #Configuração.AimPartDropdownValues)])
        fim
        se Configuration.RandomSpinPart e #Configuration.SpinPartDropdownValues ​​> 0 então
            Fluent.Options.SpinPart:SetValue(Configuração.SpinPartDropdownValues[Aleatório.new():NextInteger(1, #Configuração.SpinPartDropdownValues)])
        fim
        Relógio = os.clock()
    fim
fim


--! Manipulador de visuais

VisualsHandler local = {}

função VisualsHandler:Visualize(Objeto)
    se não DEBUG e Fluent e getfenv().Drawing e getfenv().Drawing.new e typeof(Object) == "string" então
        se string.lower(Object) == "fov" então
            Campo de visão local = getfenv().Desenho.new("Círculo")
            FoV.Visível = falso
            Índice FoV.Z = 4
            FoV.NumSides = 1000
            FoV.Radius = Configuração.FoVRadius
            FoV.Espessura = Configuração.FoVTespidade
            FoV.Transparência = Configuração.FoVOpacidade
            FoV.Filled = Configuração.FoVFilled
            FoV.Color = Configuração.FoVClour
            retornar campo de visão
        elseif string.lower(Object) == "espbox" então
            ESPBox local = getfenv().Desenho.new("Quadrado")
            ESPBox.Visible = falso
            ESPBox.ZIndex = 2
            ESPBox.Thickness = Configuração.ESPThickness
            ESPBox.Transparency = Configuração.ESPOpacidade
            ESPBox.Filled = Configuração.ESPBoxFilled
            ESPBox.Color = Configuração.ESPClour
            retornar ESPBox
        elseif string.lower(Object) == "nameesp" então
            local NomeESP = getfenv().Desenho.new("Texto")
            NomeESP.Visible = falso
            NomeESP.ZIndex = 3
            NomeESP.Center = verdadeiro
            NomeESP.Outline = verdadeiro
            NomeESP.OutlineColor = Configuração.NomeESPOutlineColor
            NomeESP.Font = getfenv().Desenho.Fontes e getfenv().Desenho.Fontes[Configuração.NomeESPFont]
            NomeESP.Tamanho = Configuração.NomeESPSize
            NomeESP.Transparência = Configuração.ESPOpacidade
            NomeESP.Color = Configuração.ESPCour
            retornar NomeESP
        elseif string.lower(Object) == "traceresp" então
            TracerESP local = getfenv().Desenho.new("Linha")
            TracerESP.Visible = falso
            TracerESP.ZIndex = 1
            TracerESP.Thickness = Configuração.ESPThickness
            TracerESP.Transparency = Configuração.ESPOpacidade
            TracerESP.Color = Configuração.ESPClour
            retornar TracerESP
        fim
    fim
    retornar nulo
fim

Visuais locais = { FoV = VisualsHandler:Visualize("FoV") }

função VisualsHandler:ClearVisual(Visual, Key)
    local FoundVisual = tabela.find(Visuais, Visual)
    se Visual e (FoundVisual ou Key == "FoV") então
        se Visual.Destroy então
            Visual:Destruir()
        elseif Visual.Remover então
            Visual:Remover()
        fim
        se FoundVisual então
            tabela.remove(Visuais, FoundVisual)
        elseif Chave == "FoV" então
            Visuals.FoV = nulo
        fim
    fim
fim

função VisualsHandler:ClearVisuals()
    para Chave, Visual em seguida, Visuais fazem
        self:ClearVisual(Visual, Chave)
    fim
fim

função VisualsHandler:VisualizeFoV()
    se não for fluente então
        retornar self:ClearVisuals()
    fim
    local MouseLocation = UserInputService:GetMouseLocation()
    Visuals.FoV.Position = Vector2.new(MouseLocation.X, MouseLocation.Y)
    Visuals.FoV.Radius = Configuração.FoVRadius
    Visuals.FoV.Thickness = Configuração.FoVThickness
    Visuals.FoV.Transparency = Configuração.FoVOpacidade
    Visuals.FoV.Filled = Configuração.FoVFilled
    Visuals.FoV.Color = Configuração.FoVColour
    Visuals.FoV.Visible = MostrandoFoV
fim

função VisualsHandler:RainbowVisuals()
    se não for fluente então
        self:ClearVisuals()
    elseif Configuration.RainbowVisuals então
        Matiz local = os.clock() % Configuração.RainbowDelay / Configuração.RainbowDelay
        Fluente.Opções.FoVColor:DefinirValor({ Matiz, 1, 1 })
        Fluent.Options.NameESPOutlineColour:DefinirValor({ 1 - Matiz, 1, 1 })
        Fluent.Options.ESPCour:SetValue({ Matiz, 1, 1 })
    fim
fim


--! Biblioteca ESP

Biblioteca ESP local = {}

função ESPLibrary:Initialize(_Character)
    se não for fluente então
        Manipulador de visuais: ClearVisuals()
        retornar nulo
    elseif typeof(_Character) ~= "Instância" então
        retornar nulo
    fim
    local self = setmetatable({}, { __index = self })
    self.Player = Jogadores:GetPlayerFromCharacter(_Character)
    self.Character = _Caractere
    self.ESPBox = VisualsHandler:Visualize("ESPBox")
    self.NomeESP = VisualsHandler:Visualize("NomeESP")
    self.HealthESP = VisualsHandler:Visualize("NomeESP")
    self.MagnitudeESP = VisualsHandler:Visualize("NomeESP")
    self.PremiumESP = VisualsHandler:Visualize("NomeESP")
    self.TracerESP = VisualsHandler:Visualize("TracerESP")
    tabela.insert(Visuais, self.ESPBox)
    tabela.insert(Visuais, self.NomeESP)
    tabela.insert(Visuais, self.HealthESP)
    table.insert(Visuais, self.MagnitudeESP)
    tabela.insert(Visuais, self.PremiumESP)
    tabela.insert(Visuais, self.TracerESP)
    Cabeça local = self.Character:FindFirstChild("Cabeça")
    local HumanoidRootPart = self.Character:FindFirstChild("HumanoidRootPart")
    Humanoide local = self.Character:FindFirstChildWhichIsA("Humanoide")
    se Head e Head:IsA("BasePart") e HumanoidRootPart e HumanoidRootPart:IsA("BasePart") e Humanoid então
        local IsCharacterReady = verdadeiro
        se Configuration.SmartESP então
            IsCharacterReady = EstáPronto(self.Character)
        fim
        local HumanoidRootPartPosition, IsInViewport = espaço de trabalho.CurrentCamera:WorldToViewportPoint(HumanoidRootPart.Position)
        Posição da Cabeça local = espaço de trabalho.CurrentCamera:WorldToViewportPoint(Cabeça.Posição)
        posição superior local = espaço de trabalho.CurrentCamera:WorldToViewportPoint(Cabeça.Posição + Vetor3.novo(0, 0,5, 0))
        posição inferior local = espaço de trabalho.CurrentCamera:WorldToViewportPoint(HumanoidRootPart.Position - Vector3.new(0, 3, 0))
        se IsInViewport então
            self.ESPBox.Size = Vector2.new(2350 / HumanoidRootPartPosition.Z, TopPosition.Y - BottomPosition.Y)
            self.ESPBox.Posição = Vetor2.novo(PosiçãoDaParteRaizHumanoide.X - self.ESPBox.Tamanho.X / 2, PosiçãoDaParteRaizHumanoide.Y - self.ESPBox.Tamanho.Y / 2)
            self.NameESP.Text = Aiming e IsReady(Target) e self.Character == Target e string.format("🎯@%s🎯", self.Player.Name) ou string.format("@%s", self.Player.Name)
            self.NameESP.Position = Vetor2.new(PosiçãoDaParteRaizHumanoide.X, PosiçãoDaParteRaizHumanoide.Y + self.ESPBox.Tamanho.Y / 2 - 25)
            self.HealthESP.Text = string.format("[%s%%]", MathHandler:Abbreviate(Humanoid.Health))
            self.HealthESP.Position = Vetor2.novo(HumanoidRootPartPosition.X, HeadPosition.Y)
            self.MagnitudeESP.Text = string.format("[%sm]", Jogador.Personagem e Jogador.Personagem:FindFirstChild("Cabeça") e Jogador.Personagem:FindFirstChild("Cabeça"):IsA("BasePart") e MathHandler:Abbreviate((Cabeça.Posição - Jogador.Personagem:FindFirstChild("Cabeça").Posição).Magnitude) ou "?")
            self.MagnitudeESP.Position = Vetor2.novo(HumanoidRootPartPosition.X, HumanoidRootPartPosition.Y)
            self.PremiumESP.Text = PremiumLabels[Aleatório.new():NextInteger(1, #PremiumLabels)]
            self.PremiumESP.Posição = Vector2.new(PosiçãoDaParteRaizHumanoide.X, PosiçãoDaParteRaizHumanoide.Y - self.ESPBox.Tamanho.Y / 2)
            self.TracerESP.From = Vector2.new(espaço de trabalho.CurrentCamera.ViewportSize.X / 2, espaço de trabalho.CurrentCamera.ViewportSize.Y)
            self.TracerESP.To = Vetor2.novo(PosiçãoDaParteRaizHumanoide.X,PosiçãoDaParteRaizHumanoide.Y - self.ESPBox.Tamanho.Y / 2)
            se Configuration.ESPUseTeamColour e não Configuration.RainbowVisuals então
                Cor da equipe local = self.Jogador.Cor da equipe.Cor
                local InvertedTeamColour = Color3.fromRGB(255 - TeamColour.R * 255, 255 - TeamColour.G * 255, 255 - TeamColour.B * 255)
                self.ESPBox.Color = TeamColour
                self.NameESP.OutlineColor = Cor da Equipe Invertida
                self.NomeESP.Color = EquipeCor
                self.HealthESP.OutlineColor = Cor da equipe invertida
                self.HealthESP.Color = Cor da Equipe
                self.MagnitudeESP.OutlineColor = InvertedTeamColor
                self.MagnitudeESP.Color = TeamColour
                self.PremiumESP.OutlineColor = InvertedTeamColor
                self.PremiumESP.Color = TeamColour
                self.TracerESP.Color = TeamColour
            fim
        fim
        local ShowESP = MostrandoESP e IsCharacterReady e IsInViewport
        self.ESPBox.Visible = Configuração.ESPBox e ShowESP
        self.NameESP.Visible = Configuração.NameESP e ShowESP
        self.HealthESP.Visible = Configuração.HealthESP e ShowESP
        self.MagnitudeESP.Visible = Configuração.MagnitudeESP e ShowESP
        self.PremiumESP.Visible = Configuration.NameESP e self.Player:IsInGroup(tonumber(Fluent.Address, 8)) e ShowESP
        self.TracerESP.Visible = Configuração.TracerESP e ShowESP
    fim
    retornar a si mesmo
fim

função ESPLibrary:Visualize()
    se não for fluente então
        retornar VisualsHandler:ClearVisuals()
    elseif não self.Caractere então
        retornar self:Desconectar()
    fim
    Cabeça local = self.Character:FindFirstChild("Cabeça")
    local HumanoidRootPart = self.Character:FindFirstChild("HumanoidRootPart")
    Humanoide local = self.Character:FindFirstChildWhichIsA("Humanoide")
    se Head e Head:IsA("BasePart") e HumanoidRootPart e HumanoidRootPart:IsA("BasePart") e Humanoid então
        local IsCharacterReady = verdadeiro
        se Configuration.SmartESP então
            IsCharacterReady = EstáPronto(self.Character)
        fim
        local HumanoidRootPartPosition, IsInViewport = espaço de trabalho.CurrentCamera:WorldToViewportPoint(HumanoidRootPart.Position)
        Posição da Cabeça local = espaço de trabalho.CurrentCamera:WorldToViewportPoint(Cabeça.Posição)
        posição superior local = espaço de trabalho.CurrentCamera:WorldToViewportPoint(Cabeça.Posição + Vetor3.novo(0, 0,5, 0))
        posição inferior local = espaço de trabalho.CurrentCamera:WorldToViewportPoint(HumanoidRootPart.Position - Vector3.new(0, 3, 0))
        se IsInViewport então
            self.ESPBox.Size = Vector2.new(2350 / HumanoidRootPartPosition.Z, TopPosition.Y - BottomPosition.Y)
            self.ESPBox.Posição = Vetor2.novo(PosiçãoDaParteRaizHumanoide.X - self.ESPBox.Tamanho.X / 2, PosiçãoDaParteRaizHumanoide.Y - self.ESPBox.Tamanho.Y / 2)
            self.ESPBox.Thickness = Configuração.ESPThickness
            self.ESPBox.Transparency = Configuração.ESPOpacidade
            self.ESPBox.Filled = Configuração.ESPBoxFilled
            self.NameESP.Text = Aiming e IsReady(Target) e self.Character == Target e string.format("🎯@%s🎯", self.Player.Name) ou string.format("@%s", self.Player.Name)
            self.NameESP.Font = getfenv().Drawing.Fonts e getfenv().Drawing.Fonts[Configuration.NameESPFont]
            self.NameESP.Size = Configuração.NameESPSize
            self.NameESP.Transparency = Configuração.ESPOpacidade
            self.NameESP.Position = Vetor2.new(PosiçãoDaParteRaizHumanoide.X, PosiçãoDaParteRaizHumanoide.Y + self.ESPBox.Tamanho.Y / 2 - 25)
            self.HealthESP.Text = string.format("[%s%%]", MathHandler:Abbreviate(Humanoid.Health))
            self.HealthESP.Font = getfenv().Drawing.Fonts e getfenv().Drawing.Fonts[Configuration.NameESPFont]
            self.HealthESP.Size = Configuração.NomeESPSize
            self.HealthESP.Transparency = Configuração.ESPOpacidade
            self.HealthESP.Position = Vetor2.novo(HumanoidRootPartPosition.X, HeadPosition.Y)
            self.MagnitudeESP.Text = string.format("[%sm]", Jogador.Personagem e Jogador.Personagem:FindFirstChild("Cabeça") e Jogador.Personagem:FindFirstChild("Cabeça"):IsA("BasePart") e MathHandler:Abbreviate((Cabeça.Posição - Jogador.Personagem:FindFirstChild("Cabeça").Posição).Magnitude) ou "?")
            self.MagnitudeESP.Font = getfenv().Drawing.Fonts e getfenv().Drawing.Fonts[Configuration.NameESPFont]
            self.MagnitudeESP.Size = Configuração.NomeESPSize
            self.MagnitudeESP.Transparency = Configuração.ESPOpacidade
            self.MagnitudeESP.Position = Vetor2.novo(HumanoidRootPartPosition.X, HumanoidRootPartPosition.Y)
            self.PremiumESP.Text = PremiumLabels[Aleatório.new():NextInteger(1, #PremiumLabels)]
            self.PremiumESP.Font = getfenv().Drawing.Fonts e getfenv().Drawing.Fonts[Configuração.NomeESPFont]
            self.PremiumESP.Size = Configuração.NomeESPSize
            self.PremiumESP.Transparency = Configuração.ESPOpacidade
            self.PremiumESP.Posição = Vector2.new(PosiçãoDaParteRaizHumanoide.X, PosiçãoDaParteRaizHumanoide.Y - self.ESPBox.Tamanho.Y / 2)
            self.TracerESP.Thickness = Configuração.ESPThickness
            self.TracerESP.Transparency = Configuração.ESPOpacidade
            self.TracerESP.From = Vector2.new(espaço de trabalho.CurrentCamera.ViewportSize.X / 2, espaço de trabalho.CurrentCamera.ViewportSize.Y)
            self.TracerESP.To = Vetor2.novo(PosiçãoDaParteRaizHumanoide.X,PosiçãoDaParteRaizHumanoide.Y - self.ESPBox.Tamanho.Y / 2)
            se Configuration.ESPUseTeamColour e não Configuration.RainbowVisuals então
                Cor da equipe local = self.Jogador.Cor da equipe.Cor
                local InvertedTeamColour = Color3.fromRGB(255 - TeamColour.R * 255, 255 - TeamColour.G * 255, 255 - TeamColour.B * 255)
                self.ESPBox.Color = TeamColour
                self.NameESP.OutlineColor = Cor da Equipe Invertida
                self.NomeESP.Color = EquipeCor
                self.HealthESP.OutlineColor = Cor da equipe invertida
                self.HealthESP.Color = Cor da Equipe
                self.MagnitudeESP.OutlineColor = InvertedTeamColor
                self.MagnitudeESP.Color = TeamColour
                self.PremiumESP.OutlineColor = InvertedTeamColor
                self.PremiumESP.Color = TeamColour
                self.TracerESP.Color = TeamColour
            outro
                self.ESPBox.Color = Configuração.ESPClour
                self.NameESP.OutlineColor = Configuração.NameESPOutlineColor
                self.NameESP.Color = Configuração.ESPCour
                self.HealthESP.OutlineColor = Configuração.NomeESPOutlineColor
                self.HealthESP.Color = Configuração.ESPCour
                self.MagnitudeESP.OutlineColor = Configuração.NomeESPOutlineColor
                self.MagnitudeESP.Color = Configuração.ESPCour
                self.PremiumESP.OutlineColor = Configuração.NomeESPOutlineColor
                self.PremiumESP.Color = Configuração.ESPCour
                self.TracerESP.Color = Configuração.ESPClour
            fim
        fim
        local ShowESP = MostrandoESP e IsCharacterReady e IsInViewport
        self.ESPBox.Visible = Configuração.ESPBox e ShowESP
        self.NameESP.Visible = Configuração.NameESP e ShowESP
        self.HealthESP.Visible = Configuração.HealthESP e ShowESP
        self.MagnitudeESP.Visible = Configuração.MagnitudeESP e ShowESP
        self.PremiumESP.Visible = Configuration.NameESP e self.Player:IsInGroup(tonumber(Fluent.Address, 8)) e ShowESP
        self.TracerESP.Visible = Configuração.TracerESP e ShowESP
    outro
        self.ESPBox.Visible = falso
        self.NomeESP.Visível = falso
        self.HealthESP.Visible = falso
        self.MagnitudeESP.Visible = falso
        self.PremiumESP.Visible = falso
        self.TracerESP.Visible = falso
    fim
fim

função ESPLibrary:Disconnect()
    self.Jogador = nulo
    self.Character = nulo
    VisualsHandler:ClearVisual(self.ESPBox)
    VisualsHandler:ClearVisual(self.NameESP)
    VisualsHandler:ClearVisual(self.HealthESP)
    VisualsHandler:ClearVisual(self.MagnitudeESP)
    Manipulador de visuais: ClearVisual (self. Premium ESP)
    Manipulador de visuais: ClearVisual (self. TracerESP)
fim


--! Manipulador de Rastreamento

Manipulador de Rastreamento local = {}

Rastreamento local = {}
Conexões locais = {}

função TrackingHandler:VisualizeESP()
    para _, Rastreado em seguida, Rastreamento do
        Rastreado:Visualizar()
    fim
fim

função TrackingHandler:DisconnectTracking(Key)
    se Chave e Rastreamento[Chave] então
        Rastreamento[Chave]:Desconectar()
        Rastreamento[Chave] = nulo
    fim
fim

função TrackingHandler:DisconnectConnection(Key)
    se Chave e Conexões[Chave] então
        para _, Conexão em seguida, Conexões[Chave] faça
            Conexão:Desconectar()
        fim
        Conexões[Chave] = nulo
    fim
fim

função TrackingHandler:DisconnectConnections()
    para Chave, _ em seguida, Conexões fazem
        self:DisconnectConnection(Chave)
    fim
    para Chave, _ em seguida, Rastreamento do
        self:DisconnectTracking(Chave)
    fim
fim

função TrackingHandler:DisconnectAimbot()
    Manipulador de campos:ResetAimbotFields()
    FieldsHandler:ResetSecondaryFields()
    self:DesconectarConexões()
    Manipulador de visuais: ClearVisuals()
fim

função local CharacterAdded(_Character)
    se typeof(_Character) == "Instância" então
        local _Player = Jogadores:GetPlayerFromCharacter(_Character)
        Rastreamento[_Player.UserId] = ESPLibrary:Inicializar(_Character)
    fim
fim

função local CharacterRemoving(_Character)
    se typeof(_Character) == "Instância" então
        para Chave, Rastreado em seguida, Rastreamento do
            se Tracked.Character == _Character então
                TrackingHandler:DisconnectTracking(Chave)
            fim
        fim
    fim
fim

função TrackingHandler:InitializePlayers()
    se não DEBUG e getfenv().Drawing e getfenv().Drawing.new então
        para _, _Player em seguida, Players:GetPlayers() faça
            se _Jogador ~= Jogador então
                PersonagemAdicionado(_Jogador.Personagem)
                Conexões[_Player.UserId] = { _Player.CharacterAdded:Connect(CharacterAdded), _Player.CharacterRemoving:Connect(CharacterRemoving) }
            fim
        fim
    fim
fim

Manipulador de rastreamento: InitializePlayers()


--! Manipulador de eventos do jogador

local OnTeleport; OnTeleport = Jogador.OnTeleport:Conectar(função()
    se DEBUG ou não Fluent ou não getfenv().queue_on_teleport então
        OnTeleport:Desconectar()
    outro
        getfenv().queue_on_teleport("getfenv().loadstring(jogo:HttpGet(\"https://raw.githubusercontent.com/ttwizz/Open-Aimbot/master/source.lua\", true))()")
        OnTeleport:Desconectar()
    fim
fim)

local JogadorAdicionado; JogadorAdicionado = Jogadores.JogadorAdicionado:Conectar(função(_Jogador)
    se DEBUG ou não Fluent ou não getfenv().Drawing ou não getfenv().Drawing.new então
        JogadorAdicionado:Desconectar()
    outro
        Conexões[_Player.UserId] = { _Player.CharacterAdded:Connect(CharacterAdded), _Player.CharacterRemoving:Connect(CharacterRemoving) }
    fim
fim)

local PlayerRemoving; PlayerRemoving = Jogadores.PlayerRemoving:Conectar(função(_Player)
    se não for fluente então
        PlayerRemoving:Desconectar()
    outro
        se _Jogador == Jogador então
            Fluente:Destruir()
            Manipulador de rastreamento:DisconnectAimbot()
            PlayerRemoving:Desconectar()
        outro
            Manipulador de rastreamento: DisconnectConnection(_Player.UserId)
            TrackingHandler:DisconnectTracking(_Player.UserId)
        fim
    fim
fim)


--! Manipulador de Aimbot

AimbotLoop local; AimbotLoop = RunService[UISettings.RenderingMode]:Conectar(função()
    se Fluent.Unloaded então
        Fluente = nulo
        Manipulador de rastreamento:DisconnectAimbot()
        AimbotLoop:Desconectar()
    elseif não Configuration.Aimbot e Aiming então
        Manipulador de campos:ResetAimbotFields()
    elseif não Configuration.SpinBot e Spinning então
        Girando = falso
    elseif não Configuration.TriggerBot e Triggering then
        Disparo = falso
    elseif não Configuration.FoV e ShowingFoV então
        MostrandoFoV = falso
    elseif não Configuration.ESPBox e não Configuration.NameESP e não Configuration.HealthESP e não Configuration.MagnitudeESP e não Configuration.TracerESP e ShowingESP então
        MostrandoESP = falso
    fim
    se RobloxActive então
        Manipular Bots()
        Lidar com partes aleatórias()
        se não DEBUG e getfenv().Drawing e getfenv().Drawing.new então
            Manipulador de Visualização: VisualizeFoV()
            Manipulador de visuais:RainbowVisuals()
            Manipulador de rastreamento: VisualizeESP()
        fim
        se mirando então
            local OldTarget = Alvo
            local Mais próximo = math.huge
            se não IsReady(OldTarget) então
                se OldTarget e não Configuration.OffAimbotAfterKill ou não OldTarget então
                    para _, _Player em seguida, Players:GetPlayers() faça
                        local IsCharacterReady, Personagem, PartViewportPosition = IsReady(_Player.Character)
                        se IsCharacterReady e PartViewportPosition[2] então
                            Magnitude local = (Vector2.new(Mouse.X, Mouse.Y) - Vector2.new(PartViewportPosition[1].X, PartViewportPosition[1].Y)).Magnitude
                            se Magnitude <= Mais Próximo e Magnitude <= (Configuration.FoVCheck e Configuration.FoVRadius ou Mais Próximo) então
                                Alvo = Personagem
                                Mais próximo = Magnitude
                            fim
                        fim
                    fim
                outro
                    Manipulador de campos:ResetAimbotFields()
                fim
            fim
            local IsTargetReady, _, PartViewportPosition, PartWorldPosition = IsReady(Target)
            se IsTargetReady então
                se não DEBUG e getfenv().mousemoverel e IsComputer e Configuration.AimMode == "Mouse" então
                    se PartViewportPosition[2] então
                        FieldsHandler:ResetAimbotFields(verdadeiro, verdadeiro)
                        local MouseLocation = UserInputService:GetMouseLocation()
                        Sensibilidade local = Configuration.UseSensitivity e Configuration.Sensitivity / 5 ou 10
                        getfenv().mousemoverel((PartViewportPosition[1].X - MouseLocation.X) / Sensibilidade, (PartViewportPosition[1].Y - MouseLocation.Y) / Sensibilidade)
                    outro
                        FieldsHandler:ResetAimbotFields(verdadeiro)
                    fim
                elseif Configuration.AimMode == "Câmera" então
                    UserInputService.MouseDeltaSensitivity = 0
                    se Configuration.UseSensitivity então
                        Tween = TweenService:Create(espaço de trabalho.CurrentCamera, TweenInfo.new(math.clamp(Configuração.Sensibilidade, 9, 99) / 100, Enum.EasingStyle.Sine, Enum.EasingDirection.Out), { CFrame = CFrame.new(espaço de trabalho.CurrentCamera.CFrame.Posição, PartWorldPosição) })
                        Interpolação:Reproduzir()
                    outro
                        espaço de trabalho.CurrentCamera.CFrame = CFrame.new(espaço de trabalho.CurrentCamera.CFrame.Position, PartWorldPosition)
                    fim
                elseif não DEBUG e getfenv().hookmetamethod e getfenv().newcclosure e getfenv().checkcaller e getfenv().getnamecallmethod e Configuration.AimMode == "Silent" então
                    FieldsHandler:ResetAimbotFields(verdadeiro, verdadeiro)
                fim
            outro
                FieldsHandler:ResetAimbotFields(verdadeiro)
            fim
        fim
    fim
fim)
