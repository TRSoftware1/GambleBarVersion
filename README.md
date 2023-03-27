# GambleBarPro Documentation

![Features](https://i.imgur.com/ao5n6Qi.png)
- Create an unlimited amount of bars, with up to 54 drinks in each.
- All names, item lores, prices, rewards, and odds are configurable.
- Ability to spawn villager entities that will open any specified bar. Villagers will not take damage or move. To remove, right-click while holding a golden carrot.
- Ability to give players any drink from any bar via command.
- "Reward Commands" that run when a player wins a drink. (Configurable for each individual drink).
- 100% customizable messages.yml file.
- Separate help menus for players and administrators.
- Maximum value for drink prices and rewards is 9,223,372,036,854,775,807.
- Support for Minecraft server versions 1.8.3 & 1.8.8
- Ability to make each drink whatever color you want. (Scroll down for available colors).
- When a player drinks a GambleBar drink, the full drinking animation will now show before the win/lose event triggers.
- Ability to reload the config files with /bar reload.
- Ability to open a bar for another player via the console. Useful to run from Citizens NPCs, while not allow players to use /bar from any location.
- Ability to put "placeholder" items in the bar inventories.
- Get in-game notifications when there is a new update out.
- Use RGB colors for all in game text. (Note: May not be available for servers with older versions).
- Configure third possible outcome, "Super lucky wins". Has its own odds of happening, own financial and command rewards.
- Command auto-tab completions.
- Custom model data support for GambleBar Drinks. An example texture pack using custom models (1-7) can be [downloaded here.](https://drive.google.com/file/d/1OyHlkO54rCZIZk66_AYgTO_7o3gA3F1d/view?usp=share_link)

![Feature List](https://i.imgur.com/KgOIRwb.png)

![Commands](https://i.imgur.com/X2goPrL.png)

Commands start with /gamblebar, but /bar and /gamble may be used instead.

- **/gamblebar help** - Opens the help menu.
- **/gamblebar** - Open the "default" bar.
- **/gamblebar (bar ID)** - Open any bar, specified by the bar ID.
- **/gamblebar give (player name) (bar ID) (drink slot)** - Give a player a GambleBar drink by specifying the bar ID and drink slot.
- **/gamblebar spawn (villager name) (bar ID)** - Spawn a villager entity that will open any bar when clicked, specified by the bar ID.
- **/gamblebar reload** - Reload the config.yml, messages.yml, and (if using a 1.8 version) villagers.yml.
- **/gamblebar open (player name) (bar ID)** - Open a bar for another player. Doesn't require the player to have permission for that bar.

![Permissions](https://i.imgur.com/LpYqJFa.png)

- **gamblebar.help** - Access to the user help menu via /gamblebar help.
- **gamblebar.open.(bar ID)** - Access to open any specified bar. (Use gamblebar.open.* to access a player for all bars).
- **gamblebar.admin.help** - Access to the admin help menu via /gamblebar help
- **gamblebar.admin.give** - Access to give a player a drink via /gamblebar give <player name> <bar ID> <drink slot>
- **gamblebar.admin.remove** - Ability to remove any GambleBar villager by right-clicking it while holding a golden carrot.
- **gamblebar.admin.spawn** - Ability to spawn a villager entity that opens bars via /gamblebar spawn <villager name> <bar ID>
- **gamblebar.admin.reload** - Ability to reload the config files with /bar reload
- **gamblebar.admin.open** - Ability to use /bar open <player name> <bar ID>
- **gamblebar.admin.updates** - Receive in-game notifications when there is a new update available.

![Configuration Files](https://i.imgur.com/EktO3iP.png)

### config.yml
```# Here are the valid colors for the "potionColor" options for the 1.11 - 1.19 version
# RED
# BLUE
# AQUA
# BLACK
# FUCHSIA
# GRAY
# GREEN
# LIME
# MAROON
# NAVY
# OLIVE
# ORANGE
# PURPLE
# SILVER
# TEAL
# WHITE
# YELLOW

# Here are the valid colors for the "potionColor" options for the 1.8 version
# LIGHT_BLUE
# BLUE
# DARK_BLUE
# MAGENTA
# ORANGE
# GREEN
# PINK
# LIGHT_PURPLE
# PURPLE
# DARK_PURPLE
# AQUA
# GRAY

# Set this to false if you don't want to get an alert when there is a new update
updateAlerts: true

# This number is how many seconds the confusion effect lasts when a player loses a drink.
# Set to 0 to disable.
drunkEffect: 10

# This number is how many seconds the blindness effect lasts when a player loses a drink.
# Set to 0 to disable.
blindnessEffect: 10

# Set this to false to disable sound effects
# If using 1.8.x server, view sound options here: https://helpch.at/docs/1.8.8/org/bukkit/Sound.html
# If using a 1.11+ server, view sound options here (Note, not all will work depending on your server version): https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Sound.html
soundEnabled: false

# This is the sound that plays if the player has a super lucky win on a drink
superWinSound: ENTITY_PLAYER_LEVELUP

# This is the sound that plays if the player wins a drink
winSound: ENTITY_PLAYER_LEVELUP

# This is the sound that plays if the player loses a drink
loseSound: ENTITY_PLAYER_HURT

# This is a list of worlds that drinking a GambleBar potion will not work in
blacklistWorlds:
- "world_nether"
- "test_world"

# The default bar is the bar opened when a player just uses "/bar"
defaultBar: mainBar

# Everything after this is the information for the bars
# Format:
# bars:
#   <barID>:
#     title: "Title of the Bar Inventory"
#     size: 9 (This number must be a multiple of 9. Minimum is 9, Maximum is 54)
#     inventory:
#       inventorySlotNumber:
#         name: "Name of the drink"
#         lore:
#         - "This is the drink's lore"
#         - "Lore Lore"
#         customModelData: 1 (Ignore if not using custom model data. Custom Model Data will override drink color.)
#         potionColor: BLUE (Check available colors in the beginning of this file)
#         price: 500 (Price of the drink, must be an integer)
#         reward: 1000 (Reward from winning the drink)
#         superLuckyReward: 2000 (Super lucky reward from winning the drink)
#         odds: 50.00 (% Odds of winning the drink. Must be a decimal number (double))
#         superLuckyOdds: 5.00 (% Odds of getting a super lucky win of the drink. Must be a decimal number (double))
#         rewardCommands:
#         - "Command to run from console when the player wins a drink"
#         - "%player% = players name and %reward% is the amount of money they won"
#         superLuckyRewardCommands:
#         - "broadcast &c%player% &fgot very lucky and won &c$%reward% &ffrom the GambleBar!"
bars:
  mainBar:
    title: "&#c90899&lD&#c90885&le&#c90875&lf&#c9085c&la&#c90848&lu&#c90835&ll&#c9081f&lt &#c91208&lB&#c92508&la&#c93808&lr"
    size: 27
    inventory:
      0:
        name: " "
        item: STAINED_GLASS_PANE
        data: 14
      1:
        name: " "
        item: STAINED_GLASS_PANE
        data: 0
      2:
        name: " "
        item: STAINED_GLASS_PANE
        data: 11
      3:
        name: " "
        item: STAINED_GLASS_PANE
        data: 14
      4:
        name: " "
        item: STAINED_GLASS_PANE
        data: 0
      5:
        name: " "
        item: STAINED_GLASS_PANE
        data: 11
      6:
        name: " "
        item: STAINED_GLASS_PANE
        data: 14
      7:
        name: " "
        item: STAINED_GLASS_PANE
        data: 0
      8:
        name: " "
        item: STAINED_GLASS_PANE
        data: 11
      9:
        name: " "
        item: STAINED_GLASS_PANE
        data: 0
      10:
        name: "&c&lBeer"
        lore:
        - "&#00eff7&lClick to buy for a chance to win!"
        - "&#00bdf7Price: &f$%price%"
        - "&#00a1f7Reward: &f$%reward%"
        - "&#007cf7Odds of winning: &f%odds%%"
        customModelData: 1
        potionColor: BLUE
        price: 500
        reward: 1000
        superLuckyReward: 2000
        odds: 50.00
        superLuckyOdds: 5.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
        superLuckyRewardCommands:
        - "broadcast &c%player% &fgot very lucky and won &c$%reward% &ffrom the GambleBar!"
      11:
        name: "&c&lWine"
        lore:
        - "&#00eff7&lClick to buy for a chance to win!"
        - "&#00bdf7Price: &f$%price%"
        - "&#00a1f7Reward: &f$%reward%"
        - "&#007cf7Odds of winning: &f%odds%%"
        customModelData: 2
        potionColor: PURPLE
        price: 1000
        reward: 2000
        superLuckyReward: 4000
        odds: 50.00
        superLuckyOdds: 5.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
        superLuckyRewardCommands:
        - "broadcast &c%player% &fgot very lucky and won &c$%reward% &ffrom the GambleBar!"
      12:
        name: "&c&lVodka"
        lore:
        - "&#00eff7&lClick to buy for a chance to win!"
        - "&#00bdf7Price: &f$%price%"
        - "&#00a1f7Reward: &f$%reward%"
        - "&#007cf7Odds of winning: &f%odds%%"
        customModelData: 3
        potionColor: GREEN
        price: 5000
        reward: 10000
        superLuckyReward: 20000
        odds: 47.50
        superLuckyOdds: 5.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
        superLuckyRewardCommands:
        - "broadcast &c%player% &fgot very lucky and won &c$%reward% &ffrom the GambleBar!"
      13:
        name: "&c&lRum"
        lore:
        - "&#00eff7&lClick to buy for a chance to win!"
        - "&#00bdf7Price: &f$%price%"
        - "&#00a1f7Reward: &f$%reward%"
        - "&#007cf7Odds of winning: &f%odds%%"
        customModelData: 4
        potionColor: GRAY
        price: 10000
        reward: 20000
        superLuckyReward: 40000
        odds: 47.50
        superLuckyOdds: 5.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
        superLuckyRewardCommands:
        - "broadcast &c%player% &fgot very lucky and won &c$%reward% &ffrom the GambleBar!"
      14:
        name: "&c&lWhiskey"
        lore:
        - "&#00eff7&lClick to buy for a chance to win!"
        - "&#00bdf7Price: &f$%price%"
        - "&#00a1f7Reward: &f$%reward%"
        - "&#007cf7Odds of winning: &f%odds%%"
        customModelData: 5
        potionColor: ORANGE
        price: 25000
        reward: 50000
        superLuckyReward: 100000
        odds: 47.50
        superLuckyOdds: 5.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
        superLuckyRewardCommands:
        - "broadcast &c%player% &fgot very lucky and won &c$%reward% &ffrom the GambleBar!"
      15:
        name: "&c&lEverclear"
        lore:
        - "&#00eff7&lClick to buy for a chance to win!"
        - "&#00bdf7Price: &f$%price%"
        - "&#00a1f7Reward: &f$%reward%"
        - "&#007cf7Odds of winning: &f%odds%%"
        customModelData: 6
        potionColor: PURPLE
        price: 50000
        reward: 100000
        superLuckyReward: 200000
        odds: 45.00
        superLuckyOdds: 5.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
        superLuckyRewardCommands:
        - "broadcast &c%player% &fgot very lucky and won &c$%reward% &ffrom the GambleBar!"
      16:
        name: "&c&lSmirnoff's Green Apple"
        lore:
        - "&#00eff7&lClick to buy for a chance to win!"
        - "&#00bdf7Price: &f$%price%"
        - "&#00a1f7Reward: &f$%reward%"
        - "&#007cf7Odds of winning: &f%odds%%"
        customModelData: 7
        potionColor: BLUE
        price: 100000
        reward: 200000
        superLuckyReward: 400000
        odds: 45.00
        superLuckyOdds: 5.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
        superLuckyRewardCommands:
        - "broadcast &c%player% &fgot very lucky and won &c$%reward% &ffrom the GambleBar!"
      17:
        name: " "
        item: STAINED_GLASS_PANE
        data: 0
      18:
        name: " "
        item: STAINED_GLASS_PANE
        data: 14
      19:
        name: " "
        item: STAINED_GLASS_PANE
        data: 0
      20:
        name: " "
        item: STAINED_GLASS_PANE
        data: 11
      21:
        name: " "
        item: STAINED_GLASS_PANE
        data: 14
      22:
        name: " "
        item: STAINED_GLASS_PANE
        data: 0
      23:
        name: " "
        item: STAINED_GLASS_PANE
        data: 11
      24:
        name: " "
        item: STAINED_GLASS_PANE
        data: 14
      25:
        name: " "
        item: STAINED_GLASS_PANE
        data: 0
      26:
        name: " "
        item: STAINED_GLASS_PANE
        data: 11
  bar2:
    title: "&c&l2nd Bar"
    size: 18
    inventory:
      0:
        name: "&c&lBud Light"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: PURPLE
        price: 500
        reward: 1000
        odds: 50.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      1:
        name: "&c&lBudweiser"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: BLUE
        price: 1000
        reward: 2000
        odds: 50.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      2:
        name: "&c&lHeineken"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: GRAY
        price: 5000
        reward: 10000
        odds: 50.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      3:
        name: "&c&lNatural Light"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: AQUA
        price: 10000
        reward: 20000
        odds: 50.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      4:
        name: "&c&lWhite Claw"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: GRAY
        price: 25000
        reward: 50000
        odds: 47.50
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      5:
        name: "&c&lTruly"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: BLUE
        price: 50000
        reward: 100000
        odds: 47.50
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      6:
        name: "&c&lRiesling"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: GREEN
        price: 100000
        reward: 200000
        odds: 45.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      7:
        name: "&c&lChardonnay"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: ORANGE
        price: 200000
        reward: 400000
        odds: 45.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      8:
        name: "&c&lSyrah"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: ORANGE
        price: 400000
        reward: 800000
        odds: 45.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      9:
        name: "&c&lBacardi"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: GREEN
        price: 600000
        reward: 1200000
        odds: 42.50
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      10:
        name: "&c&lCaptain Morgan"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: AQUA
        price: 800000
        reward: 1600000
        odds: 42.50
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      11:
        name: "&c&lSvedka"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: BLUE
        price: 1000000
        reward: 2000000
        odds: 40.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      12:
        name: "&c&lGrey Goose"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: ORANGE
        price: 1500000
        reward: 3000000
        odds: 40.00
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
      13:
        name: "&c&lBusch Light"
        lore:
        - "&c&lClick to buy for a chance to win!"
        - "&ePrice: &f$%price%"
        - "&eReward: &f$%reward%"
        - "&eOdds of winning: &f%odds%%"
        potionColor: PURPLE
        price: 2000000
        reward: 4000000
        odds: 37.50
        rewardCommands:
        - "broadcast &c%player% &fhas won &c$%reward% &ffrom the GambleBar!"
```

### messages.yml
```
# Sent to players when they try to use a function without permission
noPermission: "&cSorry, you don't have permission for this."

# Sent to console when it tries to use a player-only command
mustBePlayer: "&4YOU MUST BE A PLAYER TO USE THIS FEATURE."

# This message is sent to a player when they open one of the bar inventories
openedBar: "&eYou've opened a GambleBar!"

# Sent to a player when they buy a drink.
# %drink% = drink name, %price% = drink's price
boughtDrink: "&fYou've bought a &c%drink% &ffor &c$%price%&f."

# Sent when a player doesn't have enough money to buy a drink
# %drink% = drink name, %price% = drink's price
insufficientFunds: "&cSorry, you can't afford the &f$%price% &cfor a &f%drink%&c."

# Sent when a player wins a drink
# %reward% = the amount of $ won
drinkWin: "&eYou've won &f$%reward% &efrom winning the drink!"

# Sent when a player has a super lucky win
# %reward% = the amount of $ won
luckyDrinkWin: "&eYou've got super lucky and won &f$%reward% &efrom winning the drink!"

# Sent to a player when they lose the drink
drinkLose: "&cYou've lost your drink and feel the effects!"

# Sent to a player when they use the /bar give command and the player is invalid
playerNotFound: "&cThat player cannot be found. Check your spelling."

# Sent when a player uses the /bar give command and the bar ID or drink slot is invalid
invalidDrink: "&cDrink doesn't exist, check the bar ID and the drink slot."

# Sent when a player tries to spawn a Gambler NPC with an invalid bar ID
invalidBar: "&cInvalid bar ID. Check the config file for the bar ID."

# Sent when a player tries to spawn a Gambler NPC with an invalid name
invalidName: "&cInvalid bar name. Please try another name."

# Sent to a player when they remove a Gambler NPC (by right-click them with a golden carrot)
gamblerDeleted: "&cYou've removed the gambler NPC."

# Sent to a player when they spawn a gambler NPC
# %name% = Gambler NPC name, %barID% = the ID of the bar this NPC opens
spawnedNPC: "&fYou've spawned a Gambler NPC, &c%name%&f, who opens bar ID: &c%barID%&f."

# Sent to players when they try to open an invalid bar
# %idList% = the list of valid bar IDs
validBars: "&fThe valid bar IDs are &c%idList%&f.\nUse &c/bar help &ffor more commands."

# Sent to a player when they try to buy a drink with a full inventory
fullInventory: "&cSorry, your inventory is too full to buy a drink!"

# Sent to the command sender when they use the "/bar give" command
# %drink% = the drink's name, %player% = the player they gave it to
gaveDrink: "&fYou've given a &c%drink% &fto &c%player%&f."

# Sent to the command sender when they successfully reload with config files with /bar reload
configsReloaded: "&bGambleBarPro config files have been reloaded."

# Sent to the user if they try to drink with the item in their offhand
noOffHand: "&c&lSorry, &7you need to move this item to your main hand!"

# Sent to players with permission "gamblebar.admin.updates" when a new update is out
updateNeeded: "\n&b&lGambleBarPro &f- Version &c%newVersion% &fis out - you are still running version &c%currentVersion%&f!\n "

# Sent when a player tries to consume a drink in a blacklisted world
blacklistedWorld: "&c&lSorry&7, you cannot gamble in this world!"

# The help menu sent to server admins with "gamblebar.admin.help"
adminHelp:
- "&f&l>> &c&lGambleBar Help Menu &f&l<<"
- "&c/gamblebar &f- Open the default gambling bar."
- "&c/gamblebar <barID> &f- Open the bar with the specific bar ID."
- "&c/gamblebar help &f- Open this help menu."
- "&c/gamblebar give <player> <barID> <drinkSlot> &f- Give a player a drink, by using the drink's bar ID and it's inventory slot."
- "&c/gamblebar spawn <NPCName> <barID> &f- Spawns a villager with a custom name that will open a bar from the specified bar ID."
- "&cRemove a NPC &f- To remove a Gambler NPC, right click it with a golden carrot."
- "&c/gamblebar open <player> <barID> &f- Open a bar for another player. (Useful for Citizens NPCs)"

# The help menu sent to users with "gamblebar.help"
userHelp:
- "&f&l>> &c&lGambleBar Help Menu &f&l<<"
- "&c/gamblebar &f- Open the default gambling bar."
- "&c/gamblebar <barID> &f- Open the bar with the specific bar ID."
- "&c/gamblebar help &f- Open this help menu."
```
If using this plugin on a 1.8.x server, there will be a villagers.yml file, this is just to keep track of the NPCs.

Want to change the sound effects from this plugin? Find more here!
1.8.x Servers: https://helpch.at/docs/1.8.8/org/bukkit/Sound.html
1.11.x - 1.19 Servers: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Sound.html

If you experience an error after changing either of the config files, considering using an online yml validator tool. (For some reason, there is a formatting issue where the first line of the item lores are improperly indented on this web page, but it is not an issue in the default files.)

![Dependencies](https://i.imgur.com/WWvjJBu.png)

GambleBarPro requires that you have the Vault plugin installed on your server. [Download Vault here](https://www.spigotmc.org/resources/vault.34315/). You must also be using an economy plugin that is compatible with Vault.(EssentialsX, for example. [Full list of compatible economy plugins found here](https://www.spigotmc.org/resources/vault.34315/).)

![Compatibility](https://i.imgur.com/rORu9Yw.png)

In order for this plugin to work correctly, you must be using Java Version 8+ and using one of the following minecraft server versions

- 1.8.3
- 1.8.8
- 1.8.9
- 1.11.x
- 1.12.x
- 1.13.x
- 1.14.x
- 1.15.x
- 1.16.x
- 1.17.x
- 1.18.x
- 1.19.x

For MC 1.8.3 - 1.8.9: It is worth noting that there is a small difference in this plugin for MC 1.8.x. When a Gambler villager is spawned, there will be an invisible armor stand spawned underneath them. This is simply to keep the villager in place. For this reason, you may run into issues if you spawn a gambler villager with only 1 block of depth underneath it. You may need to have 2 blocks placed directly underneath the villager, so that they will stay still.
