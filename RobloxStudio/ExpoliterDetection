-- Go roblox studio
-- Go to workspaces 
-- Add script (ServerSideScript)
-- Copy script from here and paste!!

-- ไปที่สตูดิโอ roblox
-- ไปที่ workspace
-- เพิ่มสคริปต์ (ServerSideScript)
-- คัดลอกสคริปต์จากที่นี่และวาง

local function onCharacterAdded(character)
    local humanoid = character:WaitForChild("Humanoid")
    local function checkExploits()
        -- Check for fly exploit
        if humanoid.PlatformStand then
            humanoid.PlatformStand = false
            kickPlayer("Fly exploit detected")
        end

        -- Check for speed walk exploit
        if humanoid.WalkSpeed > 16 then
            humanoid.WalkSpeed = 16
            kickPlayer("Speed walk exploit detected")
        end

        -- Check for jump exploit
        if humanoid.JumpPower > 50 then
            humanoid.JumpPower = 50
            kickPlayer("Jump exploit detected")
        end

        -- Check for noclip exploit
        if character:FindFirstChild("HumanoidRootPart") and character:FindFirstChild("HumanoidRootPart").Anchored then
            kickPlayer("Noclip exploit detected")
        end
    end

    checkExploits()
    humanoid.StateChanged:Connect(checkExploits)
end

local function onPlayerAdded(player)
    player.CharacterAdded:Connect(onCharacterAdded)
end

game.Players.PlayerAdded:Connect(onPlayerAdded)

function kickPlayer(reason)
    -- You can customize this function to suit your needs
    -- For example, you can use the following line to kick the player:
    -- game.Players:Kick(player.UserId, reason)
    -- Or you can use a different method to handle the exploit detection
    -- such as recording logs, giving warnings, or banning the player
    print("Kicking player: " .. reason)
end

-- Additional exploit checks

game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        -- Teleport and tween exploit check
        character.DescendantAdded:Connect(function(child)
            if child:IsA("Tween") then
                kickPlayer("Teleport and tween exploit detected")
            end
        end)

        -- Exploit create gui check
        character.ChildAdded:Connect(function(child)
            if child:IsA("ScreenGui") then
                kickPlayer("Exploit create GUI detected")
            end
        end)

        -- Exploit hack to workspace check
        game.Workspace.DescendantAdded:Connect(function(descendant)
            if descendant:IsA("RemoteEvent") or descendant:IsA("RemoteFunction") then
                kickPlayer("Exploit hack to workspace detected")
            end
        end)

        -- Exploit inf health check
        local humanoid = character:WaitForChild("Humanoid")
        humanoid.Changed:Connect(function(property)
            if property == "Health" and humanoid.Health > humanoid.MaxHealth then
                kickPlayer("Exploit infinite health detected")
            end
        end)

        -- Exploit kill player check
        humanoid.Died:Connect(function()
            kickPlayer("Exploit kill player detected")
        end)

        -- Chat bypass exploit check
        player.Chatted:Connect(function(message)
            if string.find(message, "bypass") then
                kickPlayer("Chat bypass exploit detected")
            end
        end)

        -- No enemy deal damage exploit check
        character.Humanoid.TakingDamage:Connect(function(damageInfo)
            if damageInfo and damageInfo.Attacker and damageInfo.Attacker:IsA("Player") and damageInfo.Attacker ~= player then
                kickPlayer("No enemy deal damage exploit detected")
            end
        end)

        -- Exploit use remote spy check
        character.DescendantAdded:Connect(function(child)
            if child:IsA("RemoteEvent") or child:IsA("RemoteFunction") then
                child.OnServerEvent:Connect(function()
                    kickPlayer("Exploit use remote spy detected")
                end)
            end
        end)

        -- Exploit change team check
        player.TeamChanged:Connect(function(newTeam)
            if newTeam and newTeam:IsA("Team") then
                kickPlayer("Exploit change team detected")
            end
        end)

        -- Exploit tool duplication check
        character.DescendantAdded:Connect(function(child)
            if child:IsA("Tool") and child.Parent == player.Backpack then
                kickPlayer("Exploit tool duplication detected")
            end
        end)

        -- Exploit property manipulation check
        character.DescendantAdded:Connect(function(child)
            if child:IsA("BasePart") then
                local originalTransparency = child.Transparency
                child:GetPropertyChangedSignal("Transparency"):Connect(function()
                    if child.Transparency ~= originalTransparency then
                        kickPlayer("Exploit property manipulation detected")
                    end
                end)
            end
        end)

        -- Exploit script execution check
        character.DescendantAdded:Connect(function(child)
            if child:IsA("LocalScript") or child:IsA("ModuleScript") then
                kickPlayer("Exploit script execution detected")
            end
        end)

        -- Exploit audio manipulation check
        character.DescendantAdded:Connect(function(child)
            if child:IsA("Sound") or child:IsA("RemoteEvent") or child:IsA("RemoteFunction") then
                kickPlayer("Exploit audio manipulation detected")
            end
        end)
    end)
end)
