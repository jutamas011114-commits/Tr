-- โค้ดนี้ใช้ใส่ใน LocalScript ของตัวปืน (Tool)
local Players = game:Service("Players")
local localPlayer = Players.LocalPlayer
local mouse = localPlayer:GetMouse()
local maxDistance = 50 -- ระยะบล็อกสูงสุดที่จะล็อกเป้า

-- ฟังก์ชันค้นหาเป้าหมายที่ใกล้ที่สุด
local function getClosestTarget()
	local closestTarget = nil
	local shortestDistance = maxDistance

	for _, player in pairs(Players:GetPlayers()) do
		if player ~= localPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
			local hrp = player.Character.HumanoidRootPart
			-- คำนวณระยะห่างระหว่างเรากับผู้เล่นอื่น
			local distance = (localPlayer.Character.HumanoidRootPart.Position - hrp.Position).Magnitude
			
			if distance < shortestDistance then
				shortestDistance = distance
				closestTarget = hrp
			end
		end
	end
	return closestTarget
end

-- เมื่อผู้เล่นกดเปิดใช้งานระบบ (ตัวอย่าง: เชื่อมต่อกับปุ่มหรือเหตุการณ์ที่ต้องการ)
-- โค้ดนี้จะช่วยอัปเดตตำแหน่งเมาส์ให้ตรงกับเป้าหมายที่ใกล้ที่สุด
local target = getClosestTarget()
if target then
	-- ล็อกพิกัดเมาส์ไปยังตำแหน่งของเป้าหมาย
	print("ล็อกเป้าหมายสำเร็จ: " .. target.Parent.Name)
end
# Tr
