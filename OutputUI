local isMinimized = false

function CreateGui(parental)

local ScrnGui = Instance.new("ScreenGui",parental)

ScrnGui.Name = "OutputWindowABC"
ScrnGui.ResetOnSpawn = false

local Main = Instance.new("Frame",ScrnGui)
Main.Name = "Main"
Main.BorderSizePixel = 0
Main.BackgroundColor3 = Color3.new(15/255,15/255,15/255)
Main.Size = UDim2.new(0,500,0,300)
Main.Position = UDim2.new(0.5,-250,0.5,-150)
Main.Draggable = true
Main.Active = true

local Inside = Instance.new("Frame",Main)
Inside.Name = "Inside"
Inside.BorderSizePixel = 0
Inside.BackgroundColor3 = Color3.new(25/255,25/255,25/255)
Inside.Size = UDim2.new(0,500,0,270)
Inside.Position = UDim2.new(0,0,0,30)
Inside.Active = true

local Minimize = Instance.new("TextButton",Main)
Minimize.Name = "Minimize"
Minimize.BorderSizePixel = 0
Minimize.BackgroundColor3 = Color3.new(15/255,15/255,15/255)
Minimize.Size = UDim2.new(0,30,0,30)
Minimize.Position = UDim2.new(0,470,0,0)
Minimize.Text = "-"
Minimize.TextSize = 16
Minimize.TextColor3 = Color3.new(1,1,1)
Minimize.Active = true

local Title = Instance.new("TextLabel",Main)
Title.Name = "Title"
Title.BorderSizePixel = 0
Title.Size = UDim2.new(0,0,0,0)
Title.Position = UDim2.new(0,5,0,15)
Title.Text = "Output (Loading)"
Title.TextColor3 = Color3.new(1,1,1)
Title.Font = Enum.Font.BuilderSansExtraBold
Title.TextSize = 16
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Active = true

local Output = Instance.new("TextBox",Inside)

Output.Name = "Output"
Output.Text = "[LOADING]"
Output.Position = UDim2.new(0,5,0,5)
Output.Size = UDim2.new(0,490,0,230)
Output.BackgroundColor3 = Color3.new(15/255,15/255,15/255)
Output.BorderSizePixel = 0
Output.TextWrapped = false
Output.TextColor3 = Color3.new(1,1,1)
Output.ClearTextOnFocus = false
Output.Font = Enum.Font.Code
Output.TextSize = 16
Output.TextXAlignment = Enum.TextXAlignment.Left
Output.TextYAlignment = Enum.TextYAlignment.Top
Output.MultiLine = true
Output.Active = true

return {ScrnGui, Main, Inside, Minimize, Title, Output}

end

local FullTable = nil

if game:GetService("RunService"):IsClient() then
FullTable = CreateGui(game:GetService("Players").LocalPlayer:FindFirstChildWhichIsA("PlayerGui"))
else
FullTable = CreateGui(script["Parent"]["Parent"])
end

local ScrnGui = FullTable[1]
local Main = FullTable[2]
local Inside = FullTable[3]
local Minimize = FullTable[4]
local Title = FullTable[5]
local Output = FullTable[6]

pcall(function()spawn(function()
while wait() do
local OutputLogs = game:GetService("LogService"):GetLogHistory()
local ResultOutput = ""
if #OutputLogs < 15 then
for i,v in pairs(OutputLogs) do

local MessageType = ""

if v["messageType"] == Enum.MessageType.MessageOutput then
MessageType = "OUTPUT"
elseif v["messageType"] == Enum.MessageType.MessageWarning then
MessageType = "WARNING"
elseif v["messageType"] == Enum.MessageType.MessageError then
MessageType = "ERROR"
elseif v["messageType"] == Enum.MessageType.MessageInfo then
MessageType = "INFORMATION"
else
MessageType = "UNKNOWN"
end

ResultOutput = ResultOutput.."["..MessageType.."] "..v["message"].."\n"

end

else

for v=(#OutputLogs-14),#OutputLogs do

local MessageType = ""

if OutputLogs[v]["messageType"] == Enum.MessageType.MessageOutput then
MessageType = "OUTPUT"
elseif OutputLogs[v]["messageType"] == Enum.MessageType.MessageWarning then
MessageType = "WARNING"
elseif OutputLogs[v]["messageType"] == Enum.MessageType.MessageError then
MessageType = "ERROR"
elseif OutputLogs[v]["messageType"] == Enum.MessageType.MessageInfo then
MessageType = "INFORMATION"
else
MessageType = "UNKNOWN"
end

ResultOutput = ResultOutput.."["..MessageType.."] "..OutputLogs[v]["message"].."\n"

end

end

Output.Text = ResultOutput

end
end)end)

if game:GetService("RunService"):IsServer() then
Title.Text = "Output (Server)"
elseif game:GetService("RunService"):IsClient() then
Title.Text = "Output (Client)"
else
Title.Text = "Output (Unknown)"
end

Minimize.MouseButton1Click:Connect(function()
if isMinimized then
Main.Size = UDim2.new(0,500,0,300)
Inside.Visible = true
Minimize.Text = "-"
isMinimized = false
else
Main.Size = UDim2.new(0,500,0,30)
Inside.Visible = false
Minimize.Text = "+"
isMinimized = true
end
end)

game:GetService("TestService"):Message("Output Window started up.")
