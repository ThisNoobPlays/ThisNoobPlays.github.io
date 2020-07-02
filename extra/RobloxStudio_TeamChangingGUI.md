# How To Make A Team-Changing GUI In Roblox Studio
Youtube Video Iframe here
## Prerequisites
- Roblox Studio
- General Scripting Knowledge:
	- Variables
	- Functions
	- Events
	- :Connect()
	- Accessing Properties
- How to use the Roblox Studio Explorer
## Instructions
1. Enable the "Teams" service in Model > Services > Teams, click insert.
2. Add a new ScreenGUI
3. Put two  TextButtons in the ScreenGUI you just created. Set the text and name accordingly. Also enable "TextScaled" so that the text scales automatically.
4. In ReplicatedStorage, add a RemoteEvent and call it "ChangeTeamEvent".
5. Make a new localscript inside the ScreenGUI and paste in the following code. Change the code if necessary 
> local redButton = script.Parent.RedButton -- Put the name of one button here
local blueButton = script.Parent.BlueButton -- Put the name of the other button here
local event = game:GetService("ReplicatedStorage").ChangeTeamEvent -- Set to an event in ReplicatedStorage
local function redTeam()
event:FireServer("red") -- Put the team name as the argument
end
local function blueTeam()
	event:FireServer("blue") -- Put the team name as the argument
end
-- Add more functions if you have more teams
-- Add more buttons in GUI if you have more teams
-- Add more function connections if you have more teams
redButton.MouseButton1Click:Connect(redTeam) 
blueButton.MouseButton1Click:Connect(blueTeam)
-- Add more connections if needed

6. Make a new script inside ServerScriptService and paste in the following code. Adjust code as needed.
> local event = game.ReplicatedStorage.ChangeTeamEvent -- Set to the aformentioned event in ReplicatedStorage
local redTeam = game.Teams.Red -- Make variables for each of the teams you have
local blueTeam = game.Teams.Blue
local function onTeamChange(player, color)
if color == "red" then -- Make extra elseif statements if you have more teams
player.Team = redTeam -- Set the team to the team you want
else
player.Team = blueTeam
end
end
event.OnServerEvent:Connect(onTeamChange)

7. That's it. Hopefully you have been able to make it work. If you have any questions you can go to the Youtube video and ask them in the comments.




