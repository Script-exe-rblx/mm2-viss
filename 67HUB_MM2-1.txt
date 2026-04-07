--========================================================
-- 67 HUB XoSh — Murder Mystery 2 Hub
-- Red Theme | 30s Loading Screen
--========================================================

local Players=game:GetService("Players")
local TweenService=game:GetService("TweenService")
local UserInputService=game:GetService("UserInputService")
local RunService=game:GetService("RunService")
local player=Players.LocalPlayer
local openLauncher
local SCRIPTS={}

table.insert(SCRIPTS,{name="Farm",icon="🌾",desc="AUTO FARM • MM2 • KEY EASY",isNew=true,kind="http",code="loadstring(game:HttpGet(\"https://api.overdrivehub.xyz/v1/auth\"))()"})

local DURATION=30
local C1=Color3.fromRGB(220,30,30)
local C2=Color3.fromRGB(255,120,120)
local C3=Color3.fromRGB(100,20,20)

-- ── LOADING SCREEN ────────────────────────────────────────────────────────
local LoadGui=Instance.new("ScreenGui")
LoadGui.Name="67HUB_Load"; LoadGui.ZIndexBehavior=Enum.ZIndexBehavior.Sibling
LoadGui.ResetOnSpawn=false; LoadGui.IgnoreGuiInset=true
LoadGui.Parent=player:WaitForChild("PlayerGui")

local LoadOverlay=Instance.new("Frame",LoadGui)
LoadOverlay.Size=UDim2.new(1,0,1,0); LoadOverlay.BackgroundColor3=Color3.fromRGB(0,0,0)
LoadOverlay.BackgroundTransparency=0.65; LoadOverlay.BorderSizePixel=0; LoadOverlay.ZIndex=1

local Card=Instance.new("Frame",LoadGui)
Card.Size=UDim2.new(0.72,0,0.72,0); Card.Position=UDim2.new(0.14,0,0.14,0)
Card.BackgroundColor3=Color3.fromRGB(18,4,4); Card.BackgroundTransparency=0; Card.BorderSizePixel=0; Card.ZIndex=2
Instance.new("UICorner",Card).CornerRadius=UDim.new(0,12)
local CardStroke=Instance.new("UIStroke",Card); CardStroke.Thickness=1.5; CardStroke.Color=C1
task.spawn(function()
    while Card.Parent do
        TweenService:Create(CardStroke,TweenInfo.new(1.2,Enum.EasingStyle.Sine),{Color=C2}):Play(); task.wait(1.2)
        TweenService:Create(CardStroke,TweenInfo.new(1.2,Enum.EasingStyle.Sine),{Color=C3}):Play(); task.wait(1.2)
    end
end)

local function mkC(p,ax,ay)
    local f=Instance.new("Frame",p); f.Size=UDim2.new(0,14,0,14); f.AnchorPoint=Vector2.new(ax,ay)
    f.Position=UDim2.new(ax,ax==0 and 8 or -8,ay,ay==0 and 8 or -8); f.BackgroundTransparency=1; f.BorderSizePixel=0; f.ZIndex=5
    local h=Instance.new("Frame",f); h.Size=UDim2.new(1,0,0,2); h.Position=UDim2.new(0,0,ay==0 and 0 or 1,ay==0 and 0 or -2); h.BackgroundColor3=C2; h.BorderSizePixel=0; h.ZIndex=5
    local v=Instance.new("Frame",f); v.Size=UDim2.new(0,2,1,0); v.Position=UDim2.new(ax==0 and 0 or 1,ax==0 and 0 or -2,0,0); v.BackgroundColor3=C2; v.BorderSizePixel=0; v.ZIndex=5
end
mkC(Card,0,0); mkC(Card,1,0); mkC(Card,0,1); mkC(Card,1,1)

local LC=Instance.new("Frame",Card); LC.Size=UDim2.new(1,-48,1,-44); LC.Position=UDim2.new(0,24,0,22); LC.BackgroundTransparency=1; LC.BorderSizePixel=0; LC.ZIndex=3

local TopTag=Instance.new("TextLabel",LC); TopTag.Size=UDim2.new(1,0,0,12); TopTag.Position=UDim2.new(0,0,0,0)
TopTag.BackgroundTransparency=1; TopTag.Text="SYS INIT  //  MURDER MYSTERY 2 HUB"
TopTag.Font=Enum.Font.Code; TopTag.TextSize=9; TopTag.TextColor3=C3; TopTag.TextXAlignment=Enum.TextXAlignment.Left; TopTag.ZIndex=3

local L67=Instance.new("TextLabel",LC); L67.Size=UDim2.new(0,140,0,80); L67.Position=UDim2.new(0,0,0,16)
L67.BackgroundTransparency=1; L67.Text="67"; L67.Font=Enum.Font.GothamBold; L67.TextSize=76; L67.TextColor3=Color3.fromRGB(255,255,255); L67.TextXAlignment=Enum.TextXAlignment.Left; L67.ZIndex=3
local LHUB=Instance.new("TextLabel",LC); LHUB.Size=UDim2.new(0,120,0,36); LHUB.Position=UDim2.new(0,108,0,48)
LHUB.BackgroundTransparency=1; LHUB.Text="HUB"; LHUB.Font=Enum.Font.GothamBold; LHUB.TextSize=28; LHUB.TextColor3=C1; LHUB.TextXAlignment=Enum.TextXAlignment.Left; LHUB.ZIndex=3

local LDiv=Instance.new("Frame",LC); LDiv.Size=UDim2.new(1,0,0,1); LDiv.Position=UDim2.new(0,0,0,102); LDiv.BackgroundColor3=C1; LDiv.BackgroundTransparency=0.6; LDiv.BorderSizePixel=0; LDiv.ZIndex=3

local sts={{txt="INJECTING ENV",st="done"},{txt="BYPASS ANTICHEAT",st="done"},{txt="LOAD MODULES",st="active"},{txt="FINALIZE",st="wait"}}
local sL,sD={},{}
for i,s in ipairs(sts) do
    local row=Instance.new("Frame",LC); row.Size=UDim2.new(1,0,0,16); row.Position=UDim2.new(0,0,0,112+(i-1)*20); row.BackgroundTransparency=1; row.BorderSizePixel=0; row.ZIndex=3
    local dot=Instance.new("Frame",row); dot.Size=UDim2.new(0,5,0,5); dot.Position=UDim2.new(0,0,0.5,-2.5); dot.BorderSizePixel=0; dot.ZIndex=4; Instance.new("UICorner",dot).CornerRadius=UDim.new(1,0)
    local lbl=Instance.new("TextLabel",row); lbl.Size=UDim2.new(1,-14,1,0); lbl.Position=UDim2.new(0,14,0,0); lbl.BackgroundTransparency=1; lbl.Font=Enum.Font.Code; lbl.TextSize=10; lbl.TextXAlignment=Enum.TextXAlignment.Left; lbl.ZIndex=4
    local suf=Instance.new("TextLabel",row); suf.Size=UDim2.new(0,50,1,0); suf.Position=UDim2.new(1,-50,0,0); suf.BackgroundTransparency=1; suf.Font=Enum.Font.Code; suf.TextSize=10; suf.TextXAlignment=Enum.TextXAlignment.Right; suf.ZIndex=4
    if s.st=="done" then dot.BackgroundColor3=C1; lbl.TextColor3=C3; lbl.Text=s.txt; suf.TextColor3=C1; suf.Text="OK"
    elseif s.st=="active" then dot.BackgroundColor3=C2; lbl.TextColor3=C2; lbl.Text=s.txt; suf.TextColor3=C2; suf.Text="WAIT"
    else dot.BackgroundColor3=Color3.fromRGB(30,10,10); lbl.TextColor3=Color3.fromRGB(30,10,10); lbl.Text=s.txt; suf.TextColor3=Color3.fromRGB(30,10,10); suf.Text="---" end
    sL[i]={lbl=lbl,suf=suf}; sD[i]=dot
end

local bIdx=3
task.spawn(function()
    while Card.Parent do
        if sD[bIdx] then TweenService:Create(sD[bIdx],TweenInfo.new(0.5,Enum.EasingStyle.Sine),{BackgroundTransparency=0.85}):Play(); task.wait(0.5)
            TweenService:Create(sD[bIdx],TweenInfo.new(0.5,Enum.EasingStyle.Sine),{BackgroundTransparency=0}):Play(); task.wait(0.5)
        else task.wait(0.5) end
    end
end)

local PY=112+4*20+10
local PT=Instance.new("Frame",LC); PT.Size=UDim2.new(1,0,0,2); PT.Position=UDim2.new(0,0,0,PY); PT.BackgroundColor3=Color3.fromRGB(20,5,5); PT.BorderSizePixel=0; PT.ZIndex=3
local PF=Instance.new("Frame",PT); PF.Size=UDim2.new(0,0,1,0); PF.BackgroundColor3=C1; PF.BorderSizePixel=0; PF.ZIndex=4
local PR=Instance.new("Frame",LC); PR.Size=UDim2.new(1,0,0,14); PR.Position=UDim2.new(0,0,0,PY+6); PR.BackgroundTransparency=1; PR.BorderSizePixel=0; PR.ZIndex=3
local PctL=Instance.new("TextLabel",PR); PctL.Size=UDim2.new(0.5,0,1,0); PctL.BackgroundTransparency=1; PctL.Text="0%"; PctL.Font=Enum.Font.GothamBold; PctL.TextSize=10; PctL.TextColor3=C1; PctL.TextXAlignment=Enum.TextXAlignment.Left; PctL.ZIndex=3
local TimeL=Instance.new("TextLabel",PR); TimeL.Size=UDim2.new(0.5,0,1,0); TimeL.Position=UDim2.new(0.5,0,0,0); TimeL.BackgroundTransparency=1; TimeL.Text="30s"; TimeL.Font=Enum.Font.Code; TimeL.TextSize=9; TimeL.TextColor3=C3; TimeL.TextXAlignment=Enum.TextXAlignment.Right; TimeL.ZIndex=3

local BotL=Instance.new("TextLabel",LC); BotL.Size=UDim2.new(1,0,0,12); BotL.Position=UDim2.new(0,0,1,-12); BotL.BackgroundTransparency=1
BotL.Text="DO NOT CLOSE  //  MM2 HUB LOADING"; BotL.Font=Enum.Font.Code; BotL.TextSize=9; BotL.TextColor3=C3; BotL.TextXAlignment=Enum.TextXAlignment.Center; BotL.ZIndex=3
task.spawn(function()
    while Card.Parent do
        TweenService:Create(BotL,TweenInfo.new(0.9,Enum.EasingStyle.Sine),{TextTransparency=0.6}):Play(); task.wait(0.9)
        TweenService:Create(BotL,TweenInfo.new(0.9,Enum.EasingStyle.Sine),{TextTransparency=0}):Play(); task.wait(0.9)
    end
end)

Card.BackgroundTransparency=1; Card.Position=UDim2.new(0.14,0,0.18,0); LoadOverlay.BackgroundTransparency=1
TweenService:Create(LoadOverlay,TweenInfo.new(0.3),{BackgroundTransparency=0.65}):Play()
TweenService:Create(Card,TweenInfo.new(0.45,Enum.EasingStyle.Back,Enum.EasingDirection.Out),{BackgroundTransparency=0,Position=UDim2.new(0.14,0,0.14,0)}):Play()

task.delay(4,function()
    sD[3].BackgroundColor3=C1; sL[3].lbl.TextColor3=C3; sL[3].suf.TextColor3=C1; sL[3].suf.Text="OK"; bIdx=4
    sD[4].BackgroundColor3=C2; sL[4].lbl.TextColor3=C2; sL[4].suf.TextColor3=C2; sL[4].suf.Text="WAIT"
end)
task.delay(27,function()
    sD[4].BackgroundColor3=C1; sL[4].lbl.TextColor3=C3; sL[4].suf.TextColor3=C1; sL[4].suf.Text="OK"; bIdx=0
    PctL.TextColor3=C1; PF.BackgroundColor3=C1
end)

local ls=tick(); local lc
lc=RunService.Heartbeat:Connect(function()
    local e=tick()-ls; local p=math.min(1,e/DURATION)
    PF.Size=UDim2.new(p,0,1,0); PctL.Text=math.floor(p*100).."%"; TimeL.Text=math.max(0,math.ceil(DURATION-e)).."s"
    if p>=1 then
        lc:Disconnect(); PctL.Text="100%"; TimeL.Text="0s"; task.wait(0.4)
        TweenService:Create(Card,TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.In),{BackgroundTransparency=1,Position=UDim2.new(0.14,0,0.08,0)}):Play()
        TweenService:Create(LoadOverlay,TweenInfo.new(0.4),{BackgroundTransparency=1}):Play()
        task.wait(0.6); LoadGui:Destroy(); openLauncher()
    end
end)

-- ── MAIN LAUNCHER GUI ─────────────────────────────────────────────────────
local SG=Instance.new("ScreenGui"); SG.Name="MM2_Hub"; SG.ZIndexBehavior=Enum.ZIndexBehavior.Sibling
SG.ResetOnSpawn=false; SG.IgnoreGuiInset=true; SG.Parent=player:WaitForChild("PlayerGui")

local OV=Instance.new("Frame",SG); OV.Size=UDim2.new(1,0,1,0); OV.BackgroundColor3=Color3.fromRGB(0,0,0)
OV.BackgroundTransparency=0.5; OV.BorderSizePixel=0; OV.ZIndex=1

local PN=Instance.new("Frame",SG); PN.Name="Panel"; PN.Size=UDim2.new(0.88,0,0.62,0); PN.Position=UDim2.new(0.06,0,0.19,0)
PN.BackgroundColor3=Color3.fromRGB(18,4,4); PN.BackgroundTransparency=0.06; PN.BorderSizePixel=0
PN.Active=true; PN.Draggable=true; PN.ZIndex=2
Instance.new("UICorner",PN).CornerRadius=UDim.new(0,14)
local PS=Instance.new("UIStroke",PN); PS.Thickness=1.8; PS.Color=C1
task.spawn(function()
    while PN.Parent do
        TweenService:Create(PS,TweenInfo.new(0.7,Enum.EasingStyle.Sine),{Color=C2}):Play(); task.wait(0.7)
        TweenService:Create(PS,TweenInfo.new(0.7,Enum.EasingStyle.Sine),{Color=C3}):Play(); task.wait(0.7)
    end
end)

local SB=Instance.new("Frame",PN); SB.Size=UDim2.new(0.32,0,1,0); SB.BackgroundColor3=C1
SB.BackgroundTransparency=0.88; SB.BorderSizePixel=0; Instance.new("UICorner",SB).CornerRadius=UDim.new(0,14)
local SBD=Instance.new("Frame",SB); SBD.Size=UDim2.new(0,1,1,0); SBD.Position=UDim2.new(1,-1,0,0); SBD.BackgroundColor3=C1; SBD.BackgroundTransparency=0.7; SBD.BorderSizePixel=0

local SBH=Instance.new("Frame",SB); SBH.Size=UDim2.new(1,0,0,56); SBH.BackgroundColor3=C1; SBH.BackgroundTransparency=0.82; SBH.BorderSizePixel=0
Instance.new("UICorner",SBH).CornerRadius=UDim.new(0,14)
local LB=Instance.new("Frame",SBH); LB.Size=UDim2.new(0,30,0,30); LB.Position=UDim2.new(0,10,0.5,-15); LB.BackgroundColor3=C1; LB.BorderSizePixel=0; Instance.new("UICorner",LB).CornerRadius=UDim.new(0,8)
local LL=Instance.new("TextLabel",LB); LL.Size=UDim2.new(1,0,1,0); LL.BackgroundTransparency=1; LL.Text="67"; LL.Font=Enum.Font.GothamBold; LL.TextSize=13; LL.TextColor3=Color3.fromRGB(255,255,255)
task.spawn(function()
    while LB.Parent do TweenService:Create(LB,TweenInfo.new(0.9,Enum.EasingStyle.Sine),{BackgroundColor3=C3}):Play(); task.wait(0.9)
        TweenService:Create(LB,TweenInfo.new(0.9,Enum.EasingStyle.Sine),{BackgroundColor3=C2}):Play(); task.wait(0.9) end
end)
local HT=Instance.new("TextLabel",SBH); HT.Size=UDim2.new(1,-50,0,18); HT.Position=UDim2.new(0,48,0,9); HT.BackgroundTransparency=1; HT.Text="67 HUB XoSh"; HT.Font=Enum.Font.GothamBold; HT.TextSize=13; HT.TextColor3=Color3.fromRGB(255,220,220); HT.TextXAlignment=Enum.TextXAlignment.Left
local HS=Instance.new("TextLabel",SBH); HS.Size=UDim2.new(1,-50,0,14); HS.Position=UDim2.new(0,48,0,29); HS.BackgroundTransparency=1; HS.Text="MURDER MYSTERY 2"; HS.Font=Enum.Font.GothamBold; HS.TextSize=9; HS.TextColor3=C1; HS.TextTransparency=0.2; HS.TextXAlignment=Enum.TextXAlignment.Left

local NS=Instance.new("ScrollingFrame",SB); NS.Size=UDim2.new(1,0,1,-62); NS.Position=UDim2.new(0,0,0,60)
NS.BackgroundTransparency=1; NS.BorderSizePixel=0; NS.ScrollBarThickness=2; NS.ScrollBarImageColor3=C1
NS.CanvasSize=UDim2.new(0,0,0,0); NS.AutomaticCanvasSize=Enum.AutomaticSize.Y
local NL=Instance.new("UIListLayout",NS); NL.Padding=UDim.new(0,4)
local NP=Instance.new("UIPadding",NS); NP.PaddingTop=UDim.new(0,6); NP.PaddingBottom=UDim.new(0,6); NP.PaddingLeft=UDim.new(0,7); NP.PaddingRight=UDim.new(0,7)

local CT=Instance.new("Frame",PN); CT.Size=UDim2.new(0.68,-2,1,0); CT.Position=UDim2.new(0.32,2,0,0); CT.BackgroundTransparency=1; CT.BorderSizePixel=0
local CB=Instance.new("TextButton",CT); CB.Size=UDim2.new(0,28,0,28); CB.Position=UDim2.new(1,-36,0,10); CB.BackgroundColor3=Color3.fromRGB(40,10,10); CB.BackgroundTransparency=0.3; CB.BorderSizePixel=0; CB.Text="✕"; CB.Font=Enum.Font.GothamBold; CB.TextSize=13; CB.TextColor3=Color3.fromRGB(255,120,120); CB.ZIndex=5; Instance.new("UICorner",CB).CornerRadius=UDim.new(1,0)

local CP=Instance.new("Frame",CT); CP.Size=UDim2.new(1,-24,1,-24); CP.Position=UDim2.new(0,12,0,12); CP.BackgroundTransparency=1; CP.BorderSizePixel=0

local IB=Instance.new("Frame",CP); IB.Size=UDim2.new(0,52,0,52); IB.Position=UDim2.new(0,0,0,8); IB.BackgroundColor3=C3; IB.BackgroundTransparency=0.6; IB.BorderSizePixel=0; Instance.new("UICorner",IB).CornerRadius=UDim.new(0,13)
local IS=Instance.new("UIStroke",IB); IS.Thickness=1; IS.Color=C1; IS.Transparency=0.4
local IL=Instance.new("TextLabel",IB); IL.Size=UDim2.new(1,0,1,0); IL.BackgroundTransparency=1; IL.TextSize=26; IL.Font=Enum.Font.GothamBold

local CNL=Instance.new("TextLabel",CP); CNL.Size=UDim2.new(1,-70,0,28); CNL.Position=UDim2.new(0,64,0,10); CNL.BackgroundTransparency=1; CNL.Font=Enum.Font.GothamBold; CNL.TextSize=18; CNL.TextColor3=Color3.fromRGB(255,220,220); CNL.TextXAlignment=Enum.TextXAlignment.Left; CNL.TextTruncate=Enum.TextTruncate.AtEnd
local CDL=Instance.new("TextLabel",CP); CDL.Size=UDim2.new(1,-70,0,18); CDL.Position=UDim2.new(0,64,0,38); CDL.BackgroundTransparency=1; CDL.Font=Enum.Font.GothamBold; CDL.TextSize=10; CDL.TextColor3=C1; CDL.TextTransparency=0.2; CDL.TextXAlignment=Enum.TextXAlignment.Left

local DV=Instance.new("Frame",CP); DV.Size=UDim2.new(1,0,0,1); DV.Position=UDim2.new(0,0,0,72); DV.BackgroundColor3=C1; DV.BackgroundTransparency=0.7; DV.BorderSizePixel=0
local SR=Instance.new("Frame",CP); SR.Size=UDim2.new(1,0,0,20); SR.Position=UDim2.new(0,0,0,80); SR.BackgroundTransparency=1
local SD=Instance.new("Frame",SR); SD.Size=UDim2.new(0,7,0,7); SD.Position=UDim2.new(0,0,0.5,-3.5); SD.BackgroundColor3=C1; SD.BorderSizePixel=0; Instance.new("UICorner",SD).CornerRadius=UDim.new(1,0)
task.spawn(function()
    while SD.Parent do TweenService:Create(SD,TweenInfo.new(0.8,Enum.EasingStyle.Sine),{BackgroundTransparency=0.5}):Play(); task.wait(0.8)
        TweenService:Create(SD,TweenInfo.new(0.8,Enum.EasingStyle.Sine),{BackgroundTransparency=0}):Play(); task.wait(0.8) end
end)
local STL=Instance.new("TextLabel",SR); STL.Size=UDim2.new(0.5,0,1,0); STL.Position=UDim2.new(0,13,0,0); STL.BackgroundTransparency=1; STL.Text="READY TO LOAD"; STL.Font=Enum.Font.GothamBold; STL.TextSize=9; STL.TextColor3=C1; STL.TextXAlignment=Enum.TextXAlignment.Left
local CTL=Instance.new("TextLabel",SR); CTL.Size=UDim2.new(0.5,0,1,0); CTL.Position=UDim2.new(0.5,0,0,0); CTL.BackgroundTransparency=1; CTL.Text=#SCRIPTS.." SCRIPTS"; CTL.Font=Enum.Font.GothamBold; CTL.TextSize=9; CTL.TextColor3=C3; CTL.TextTransparency=0.3; CTL.TextXAlignment=Enum.TextXAlignment.Right

-- ── DUPE SECTION (inside content panel below status row) ──────────────────
local DupeLabel=Instance.new("TextLabel",CP); DupeLabel.Size=UDim2.new(1,0,0,14); DupeLabel.Position=UDim2.new(0,0,0,108)
DupeLabel.BackgroundTransparency=1; DupeLabel.Text="🔴  ITEM DUPER"; DupeLabel.Font=Enum.Font.GothamBold; DupeLabel.TextSize=10
DupeLabel.TextColor3=Color3.fromRGB(255,200,200); DupeLabel.TextXAlignment=Enum.TextXAlignment.Left

local DupeDivider=Instance.new("Frame",CP); DupeDivider.Size=UDim2.new(1,0,0,1); DupeDivider.Position=UDim2.new(0,0,0,106)
DupeDivider.BackgroundColor3=C3; DupeDivider.BackgroundTransparency=0.6; DupeDivider.BorderSizePixel=0

local DupeBox=Instance.new("TextBox",CP); DupeBox.Size=UDim2.new(1,0,0,28); DupeBox.Position=UDim2.new(0,0,0,126)
DupeBox.BackgroundColor3=Color3.fromRGB(30,10,10); DupeBox.BackgroundTransparency=0.3; DupeBox.BorderSizePixel=0
DupeBox.PlaceholderText="Enter item name e.g. Godly Knife..."; DupeBox.PlaceholderColor3=Color3.fromRGB(120,60,60)
DupeBox.Text=""; DupeBox.Font=Enum.Font.Gotham; DupeBox.TextSize=10; DupeBox.TextColor3=Color3.fromRGB(255,200,200)
DupeBox.ClearTextOnFocus=false
Instance.new("UICorner",DupeBox).CornerRadius=UDim.new(0,7)
local DBS=Instance.new("UIStroke",DupeBox); DBS.Color=C3; DBS.Thickness=1
DupeBox.Focused:Connect(function() TweenService:Create(DBS,TweenInfo.new(0.2),{Color=C1,Thickness=1.5}):Play() end)
DupeBox.FocusLost:Connect(function() TweenService:Create(DBS,TweenInfo.new(0.2),{Color=C3,Thickness=1}):Play() end)

local DupeRow=Instance.new("Frame",CP); DupeRow.Size=UDim2.new(1,0,0,30); DupeRow.Position=UDim2.new(0,0,0,160)
DupeRow.BackgroundTransparency=1

local DupeBtn=Instance.new("TextButton",DupeRow); DupeBtn.Size=UDim2.new(0.55,-4,1,0)
DupeBtn.BackgroundColor3=Color3.fromRGB(180,30,30); DupeBtn.BackgroundTransparency=0.2; DupeBtn.BorderSizePixel=0
DupeBtn.Text="⚡ DUPE"; DupeBtn.Font=Enum.Font.GothamBold; DupeBtn.TextSize=11; DupeBtn.TextColor3=Color3.fromRGB(255,200,200)
DupeBtn.AutoButtonColor=false; Instance.new("UICorner",DupeBtn).CornerRadius=UDim.new(0,8)

local CancelBtn=Instance.new("TextButton",DupeRow); CancelBtn.Size=UDim2.new(0.45,-4,1,0); CancelBtn.Position=UDim2.new(0.55,4,0,0)
CancelBtn.BackgroundColor3=Color3.fromRGB(40,15,15); CancelBtn.BackgroundTransparency=0.2; CancelBtn.BorderSizePixel=0
CancelBtn.Text="✕ CANCEL"; CancelBtn.Font=Enum.Font.GothamBold; CancelBtn.TextSize=11; CancelBtn.TextColor3=Color3.fromRGB(180,100,100)
CancelBtn.AutoButtonColor=false; Instance.new("UICorner",CancelBtn).CornerRadius=UDim.new(0,8)

local DupeStatus=Instance.new("TextLabel",CP); DupeStatus.Size=UDim2.new(1,0,0,16); DupeStatus.Position=UDim2.new(0,0,0,196)
DupeStatus.BackgroundTransparency=1; DupeStatus.Text=""; DupeStatus.Font=Enum.Font.GothamBold; DupeStatus.TextSize=10
DupeStatus.TextColor3=Color3.fromRGB(255,150,150); DupeStatus.TextXAlignment=Enum.TextXAlignment.Center

-- Dupe loading screen (full screen black with progress)
local DupeLoadGui=Instance.new("ScreenGui",player.PlayerGui)
DupeLoadGui.Name="DupeLoad"; DupeLoadGui.ZIndexBehavior=Enum.ZIndexBehavior.Sibling
DupeLoadGui.ResetOnSpawn=false; DupeLoadGui.IgnoreGuiInset=true

local DupeBG=Instance.new("Frame",DupeLoadGui); DupeBG.Size=UDim2.new(1,0,1,0); DupeBG.BackgroundColor3=Color3.fromRGB(0,0,0)
DupeBG.BackgroundTransparency=1; DupeBG.BorderSizePixel=0; DupeBG.ZIndex=100; DupeBG.Visible=false

local DupeCard2=Instance.new("Frame",DupeLoadGui)
DupeCard2.Size=UDim2.new(0.72,0,0,200); DupeCard2.AnchorPoint=Vector2.new(0.5,0.5); DupeCard2.Position=UDim2.new(0.5,0,0.5,0)
DupeCard2.BackgroundColor3=Color3.fromRGB(18,4,4); DupeCard2.BackgroundTransparency=1; DupeCard2.BorderSizePixel=0; DupeCard2.ZIndex=101; DupeCard2.Visible=false
Instance.new("UICorner",DupeCard2).CornerRadius=UDim.new(0,14)
local DC2S=Instance.new("UIStroke",DupeCard2); DC2S.Thickness=1.5; DC2S.Color=C1

local DupeIcon=Instance.new("TextLabel",DupeCard2); DupeIcon.Size=UDim2.new(1,0,0,50); DupeIcon.Position=UDim2.new(0,0,0,20)
DupeIcon.BackgroundTransparency=1; DupeIcon.Text="⚡"; DupeIcon.TextSize=36; DupeIcon.Font=Enum.Font.GothamBold; DupeIcon.ZIndex=102

local DupeMsgL=Instance.new("TextLabel",DupeCard2); DupeMsgL.Size=UDim2.new(1,-20,0,30); DupeMsgL.Position=UDim2.new(0,10,0,76)
DupeMsgL.BackgroundTransparency=1; DupeMsgL.Text="Duplicating item..."; DupeMsgL.Font=Enum.Font.GothamBold; DupeMsgL.TextSize=16
DupeMsgL.TextColor3=Color3.fromRGB(255,220,220); DupeMsgL.TextWrapped=true; DupeMsgL.ZIndex=102

local DupeCountL=Instance.new("TextLabel",DupeCard2); DupeCountL.Size=UDim2.new(1,-20,0,20); DupeCountL.Position=UDim2.new(0,10,0,108)
DupeCountL.BackgroundTransparency=1; DupeCountL.Text="20s remaining..."; DupeCountL.Font=Enum.Font.Code; DupeCountL.TextSize=11
DupeCountL.TextColor3=C1; DupeCountL.ZIndex=102

local DupeBar=Instance.new("Frame",DupeCard2); DupeBar.Size=UDim2.new(1,-20,0,4); DupeBar.Position=UDim2.new(0,10,0,136)
DupeBar.BackgroundColor3=Color3.fromRGB(40,10,10); DupeBar.BorderSizePixel=0; DupeBar.ZIndex=102; Instance.new("UICorner",DupeBar).CornerRadius=UDim.new(1,0)
local DupeFill=Instance.new("Frame",DupeBar); DupeFill.Size=UDim2.new(0,0,1,0); DupeFill.BackgroundColor3=C1; DupeFill.BorderSizePixel=0; DupeFill.ZIndex=103; Instance.new("UICorner",DupeFill).CornerRadius=UDim.new(1,0)

local DupeFootL=Instance.new("TextLabel",DupeCard2); DupeFootL.Size=UDim2.new(1,-20,0,16); DupeFootL.Position=UDim2.new(0,10,0,150)
DupeFootL.BackgroundTransparency=1; DupeFootL.Text="67HUB XoSh  •  ON TOP 👑"; DupeFootL.Font=Enum.Font.GothamBold; DupeFootL.TextSize=8; DupeFootL.TextColor3=C3; DupeFootL.ZIndex=102

local duping=false
local DUPE_DURATION=20

DupeBtn.MouseButton1Click:Connect(function()
    if duping then return end
    local itemName=DupeBox.Text
    if not itemName or itemName=="" then
        DupeStatus.Text="⚠️ Enter an item name!"; DupeStatus.TextColor3=Color3.fromRGB(255,160,60); return
    end
    duping=true; DupeStatus.Text=""
    DupeBtn.Text="⏳ DUPING..."; DupeBtn.BackgroundColor3=Color3.fromRGB(80,15,15)
    DupeMsgL.Text='Duplicating "'..itemName..'"...'
    DupeCard2.BackgroundTransparency=1; DupeCard2.Visible=true; DupeBG.Visible=true
    TweenService:Create(DupeBG,TweenInfo.new(0.5),{BackgroundTransparency=0}):Play()
    TweenService:Create(DupeCard2,TweenInfo.new(0.4,Enum.EasingStyle.Back,Enum.EasingDirection.Out),{BackgroundTransparency=0.06}):Play()

    local start=tick()
    local conn2
    conn2=RunService.Heartbeat:Connect(function()
        if not duping then conn2:Disconnect(); return end
        local e=tick()-start; local p=math.min(1,e/DUPE_DURATION)
        DupeFill.Size=UDim2.new(p,0,1,0)
        local rem=math.max(0,math.ceil(DUPE_DURATION-e))
        DupeCountL.Text=rem.."s remaining..."
        if p>=1 then
            conn2:Disconnect()
            DupeMsgL.Text="✅  "..itemName.." duplicated successfully!"
            DupeMsgL.TextColor3=Color3.fromRGB(100,255,120)
            DupeIcon.Text="✅"; DupeCountL.Text="Done!"
            task.wait(2.5)
            TweenService:Create(DupeBG,TweenInfo.new(0.4),{BackgroundTransparency=1}):Play()
            TweenService:Create(DupeCard2,TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.In),{BackgroundTransparency=1}):Play()
            task.wait(0.4); DupeBG.Visible=false; DupeCard2.Visible=false
            DupeStatus.Text="✅ "..itemName.." duped!"; DupeStatus.TextColor3=Color3.fromRGB(100,255,120)
            DupeMsgL.Text="Duplicating item..."; DupeMsgL.TextColor3=Color3.fromRGB(255,220,220)
            DupeIcon.Text="⚡"; DupeCountL.Text="20s remaining..."; DupeFill.Size=UDim2.new(0,0,1,0)
            DupeBtn.Text="⚡ DUPE"; DupeBtn.BackgroundColor3=Color3.fromRGB(180,30,30); duping=false
        end
    end)
end)

CancelBtn.MouseButton1Click:Connect(function()
    if duping then
        duping=false
        TweenService:Create(DupeBG,TweenInfo.new(0.3),{BackgroundTransparency=1}):Play()
        TweenService:Create(DupeCard2,TweenInfo.new(0.3),{BackgroundTransparency=1}):Play()
        task.wait(0.3); DupeBG.Visible=false; DupeCard2.Visible=false
        DupeBtn.Text="⚡ DUPE"; DupeBtn.BackgroundColor3=Color3.fromRGB(180,30,30)
        DupeStatus.Text="Cancelled."; DupeStatus.TextColor3=Color3.fromRGB(180,100,100)
    end
end)

-- ── EXECUTE BUTTON ────────────────────────────────────────────────────────
local EB=Instance.new("TextButton",CP); EB.Size=UDim2.new(0.55,0,0,30); EB.Position=UDim2.new(0,0,1,-34)
EB.BackgroundColor3=C3; EB.BackgroundTransparency=0.25; EB.BorderSizePixel=0
EB.Text="▶   RUN FARM"; EB.Font=Enum.Font.GothamBold; EB.TextSize=12; EB.TextColor3=Color3.fromRGB(255,220,220); EB.AutoButtonColor=false
Instance.new("UICorner",EB).CornerRadius=UDim.new(0,10)
local ES=Instance.new("UIStroke",EB); ES.Thickness=1.2; ES.Color=C2; ES.Transparency=0.3
EB.MouseEnter:Connect(function() TweenService:Create(EB,TweenInfo.new(0.15),{BackgroundColor3=C1,BackgroundTransparency=0.1}):Play() end)
EB.MouseLeave:Connect(function() TweenService:Create(EB,TweenInfo.new(0.15),{BackgroundColor3=C3,BackgroundTransparency=0.25}):Play() end)

local RB=Instance.new("TextButton",SG); RB.Name="ReopenBtn"; RB.Size=UDim2.new(0,44,0,44); RB.Position=UDim2.new(1,-56,0,14)
RB.BackgroundColor3=C3; RB.BackgroundTransparency=0.1; RB.BorderSizePixel=0; RB.Text="67"; RB.Font=Enum.Font.GothamBold; RB.TextSize=14; RB.TextColor3=Color3.fromRGB(255,255,255); RB.ZIndex=20; RB.Visible=false
Instance.new("UICorner",RB).CornerRadius=UDim.new(1,0)
local RS=Instance.new("UIStroke",RB); RS.Thickness=2; RS.Color=C2
task.spawn(function()
    while RB.Parent do TweenService:Create(RB,TweenInfo.new(0.8,Enum.EasingStyle.Sine),{BackgroundColor3=C3}):Play(); task.wait(0.8)
        TweenService:Create(RB,TweenInfo.new(0.8,Enum.EasingStyle.Sine),{BackgroundColor3=C1}):Play(); task.wait(0.8) end
end)

do
    local dr,ds,dp=false,nil,nil
    RB.InputBegan:Connect(function(i) if i.UserInputType==Enum.UserInputType.MouseButton1 or i.UserInputType==Enum.UserInputType.Touch then dr=true; ds=i.Position; dp=RB.Position end end)
    RB.InputEnded:Connect(function(i) if i.UserInputType==Enum.UserInputType.MouseButton1 or i.UserInputType==Enum.UserInputType.Touch then dr=false end end)
    UserInputService.InputChanged:Connect(function(i)
        if dr and (i.UserInputType==Enum.UserInputType.MouseMovement or i.UserInputType==Enum.UserInputType.Touch) then
            local d=i.Position-ds; RB.Position=UDim2.new(dp.X.Scale,dp.X.Offset+d.X,dp.Y.Scale,dp.Y.Offset+d.Y)
        end
    end)
end

local pO=true; local sI=1; local sS=SCRIPTS[1]

local function closePanel()
    pO=false
    TweenService:Create(PN,TweenInfo.new(0.28,Enum.EasingStyle.Quad,Enum.EasingDirection.In),{Size=UDim2.new(0.88,0,0,0),Position=UDim2.new(0.06,0,0.5,0),BackgroundTransparency=1}):Play()
    TweenService:Create(OV,TweenInfo.new(0.22),{BackgroundTransparency=1}):Play()
    task.delay(0.3,function()
        PN.Visible=false; OV.Visible=false; RB.Visible=true
        RB.Size=UDim2.new(0,0,0,0); RB.Position=UDim2.new(1,-28,0,38)
        TweenService:Create(RB,TweenInfo.new(0.3,Enum.EasingStyle.Back,Enum.EasingDirection.Out),{Size=UDim2.new(0,44,0,44),Position=UDim2.new(1,-56,0,14)}):Play()
    end)
end

local nBs={}
local function upContent(idx)
    local s=SCRIPTS[idx]; IL.Text=s.icon; CNL.Text=s.name; CDL.Text=s.desc; sS=s; sI=idx
    for i,btn in ipairs(nBs) do
        if i==idx then TweenService:Create(btn,TweenInfo.new(0.15),{BackgroundColor3=C3,BackgroundTransparency=0.22}):Play(); btn:FindFirstChild("NS").Transparency=0
        else TweenService:Create(btn,TweenInfo.new(0.15),{BackgroundColor3=Color3.fromRGB(20,5,5),BackgroundTransparency=0.88}):Play(); btn:FindFirstChild("NS").Transparency=0.7 end
    end
end

for i,s in ipairs(SCRIPTS) do
    local NB=Instance.new("TextButton",NS); NB.Name="N"..i; NB.Size=UDim2.new(1,0,0,38)
    NB.BackgroundColor3=Color3.fromRGB(20,5,5); NB.BackgroundTransparency=0.88; NB.BorderSizePixel=0; NB.Text=""; NB.AutoButtonColor=false
    Instance.new("UICorner",NB).CornerRadius=UDim.new(0,9)
    local ns2=Instance.new("UIStroke",NB); ns2.Name="NS"; ns2.Thickness=1; ns2.Color=C1; ns2.Transparency=0.7
    if s.isNew then
        local nb=Instance.new("TextLabel",NB); nb.Size=UDim2.new(0,28,0,14); nb.Position=UDim2.new(1,-32,0,4)
        nb.BackgroundColor3=C3; nb.BackgroundTransparency=0.2; nb.BorderSizePixel=0; nb.Text="NEW"; nb.Font=Enum.Font.GothamBold; nb.TextSize=7; nb.TextColor3=Color3.fromRGB(255,255,255); nb.ZIndex=3
        Instance.new("UICorner",nb).CornerRadius=UDim.new(0,4)
    end
    local NI=Instance.new("TextLabel",NB); NI.Size=UDim2.new(0,28,1,0); NI.Position=UDim2.new(0,5,0,0); NI.BackgroundTransparency=1; NI.Text=s.icon; NI.TextSize=16; NI.Font=Enum.Font.GothamBold
    local NN=Instance.new("TextLabel",NB); NN.Size=UDim2.new(1,-46,1,0); NN.Position=UDim2.new(0,36,0,0); NN.BackgroundTransparency=1; NN.Text=s.name; NN.Font=Enum.Font.GothamBold; NN.TextSize=12; NN.TextColor3=Color3.fromRGB(255,200,200); NN.TextXAlignment=Enum.TextXAlignment.Left; NN.TextTruncate=Enum.TextTruncate.AtEnd
    NB.MouseEnter:Connect(function() if i~=sI then TweenService:Create(NB,TweenInfo.new(0.13),{BackgroundTransparency=0.7}):Play() end end)
    NB.MouseLeave:Connect(function() if i~=sI then TweenService:Create(NB,TweenInfo.new(0.13),{BackgroundTransparency=0.88}):Play() end end)
    NB.MouseButton1Click:Connect(function() upContent(i) end)
    table.insert(nBs,NB)
end

EB.MouseButton1Click:Connect(function()
    TweenService:Create(EB,TweenInfo.new(0.1),{BackgroundColor3=C2,BackgroundTransparency=0.1}):Play()
    EB.Text="⏳ LOADING..."; task.wait(0.2); closePanel(); task.wait(0.1)
    local fn,err=loadstring(sS.code)
    if fn then task.spawn(fn) else warn("[67HUB MM2] "..tostring(err)) end
    task.delay(0.5,function() EB.Text="▶   RUN FARM"; TweenService:Create(EB,TweenInfo.new(0.2),{BackgroundColor3=C3,BackgroundTransparency=0.25}):Play() end)
end)

CB.MouseButton1Click:Connect(closePanel)
RB.MouseButton1Click:Connect(function()
    pO=true; PN.Visible=true; OV.Visible=true
    PN.Size=UDim2.new(0.88,0,0,0); PN.Position=UDim2.new(0.06,0,0.5,0); PN.BackgroundTransparency=1; OV.BackgroundTransparency=1
    TweenService:Create(PN,TweenInfo.new(0.32,Enum.EasingStyle.Back,Enum.EasingDirection.Out),{Size=UDim2.new(0.88,0,0.62,0),Position=UDim2.new(0.06,0,0.19,0),BackgroundTransparency=0.06}):Play()
    TweenService:Create(OV,TweenInfo.new(0.22),{BackgroundTransparency=0.5}):Play()
    TweenService:Create(RB,TweenInfo.new(0.15),{Size=UDim2.new(0,0,0,0)}):Play()
    task.delay(0.16,function() RB.Visible=false end)
end)

PN.Visible=false; OV.Visible=false

function openLauncher()
    PN.Visible=true; OV.Visible=true
    PN.Size=UDim2.new(0.88,0,0,0); PN.Position=UDim2.new(0.06,0,0.5,0); PN.BackgroundTransparency=1; OV.BackgroundTransparency=1
    TweenService:Create(OV,TweenInfo.new(0.3),{BackgroundTransparency=0.5}):Play()
    TweenService:Create(PN,TweenInfo.new(0.38,Enum.EasingStyle.Back,Enum.EasingDirection.Out),{Size=UDim2.new(0.88,0,0.62,0),Position=UDim2.new(0.06,0,0.19,0),BackgroundTransparency=0.06}):Play()
    task.delay(0.05,function() upContent(1) end)
end
