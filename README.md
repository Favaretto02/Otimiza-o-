loadstring([[
-- Melhorias gráficas e desempenho
local lighting = game:GetService("Lighting")
local workspace = game:GetService("Workspace")

-- Ajuste para qualidade gráfica sem travamentos
lighting.GlobalShadows = true           -- Ativa as sombras
lighting.Brightness = 2                 -- Intensidade da luz
lighting.OutdoorAmbient = Color3.fromRGB(170, 170, 170)  -- Ajusta a luz ambiente para maior visibilidade
lighting.FogStart = 50                  -- Distância do início da neblina
lighting.FogEnd = 1000                  -- Distância do final da neblina
lighting.Ambient = Color3.fromRGB(200, 200, 200)  -- Ajusta o ambiente da iluminação

-- Desativa algumas funções para reduzir o lag sem comprometer tanto a qualidade
game:GetService("UserSettings").GameSettings.GraphicsQuality = Enum.QualityLevel.Level2  -- Define qualidade gráfica para intermediário

-- Ajustes de água para melhorar a performance sem perder qualidade
workspace.Terrain.WaterWaveSize = 0.25  -- Reduz o tamanho das ondas, diminuindo o processamento
workspace.Terrain.WaterWaveSpeed = 5    -- Ajusta a velocidade das ondas
workspace.Terrain.WaterReflectance = 0.5  -- Reflexão da água
workspace.Terrain.WaterTransparency = 0.3  -- Transparência da água

-- Ativa partículas e efeitos leves para manter o gráfico bonito
for _, obj in pairs(workspace:GetDescendants()) do
    if obj:IsA("ParticleEmitter") or obj:IsA("Trail") then
        obj.Enabled = true
    end
end

-- Ajustes de qualidade de partículas e efeitos
local particles = game:GetService("ReplicatedStorage"):FindFirstChild("Particles")
if particles then
    for _, particle in pairs(particles:GetChildren()) do
        particle:Destroy()  -- Remove partículas extras que podem gerar lag
    end
end

-- Aviso de melhorias gráficas
game.StarterGui:SetCore("ChatMakeSystemMessage", {
    Text = "[INFO] Gráficos Otimizados e Melhorados!";
    Color = Color3.fromRGB(0, 255, 0);
    Font = Enum.Font.SourceSansBold;
    FontSize = Enum.FontSize.Size24;
})
]])()
# Otimiza-o-
Script de otimização gráfica para Roblox
