-- Script para criar um painel funcional no Roblox

local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local PlantButton = Instance.new("TextButton")
local HarvestButton = Instance.new("TextButton")

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

Frame.Size = UDim2.new(0.3, 0, 0.3, 0)
Frame.Position = UDim2.new(0.35, 0, 0.35, 0)
Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame.Parent = ScreenGui

PlantButton.Size = UDim2.new(0.8, 0, 0.4, 0)
PlantButton.Position = UDim2.new(0.1, 0, 0.1, 0)
PlantButton.Text = "Plantar"
PlantButton.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
PlantButton.Parent = Frame

HarvestButton.Size = UDim2.new(0.8, 0, 0.4, 0)
HarvestButton.Position = UDim2.new(0.1, 0, 0.5, 0)
HarvestButton.Text = "Colher"
HarvestButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
HarvestButton.Parent = Frame

local function createPlant()
    local plant = Instance.new("Part")
    plant.Size = Vector3.new(2, 2, 2)
    plant.Anchored = true
    plant.Position = Vector3.new(0, 1, 0)
    plant.Parent = workspace
    return plant
end

local function growPlant(plant)
    for i = 1, 5 do
        plant.Size = plant.Size + Vector3.new(0, 1, 0)
        wait(1)
    end
end

local function harvestPlant(plant)
    plant:Destroy()
    print("Planta colhida!")
end

PlantButton.MouseButton1Click:Connect(function()
    local plant = createPlant()
    growPlant(plant)
end)

HarvestButton.MouseButton1Click:Connect(function()
    local plant = workspace:FindFirstChild("Part")
    if plant then
        harvestPlant(plant)
    end
end)
