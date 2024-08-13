# **arma3mercenaries Enhanced Kill Script: Kill Notification, Kill Reward, & Death Marker System**

                     __..-----')
         ,.--._ .-'_..--...-'
        '-"'. _/_ /  ..--''""'-.
        _.--""...:._:(_ ..:"::. \
     .-' ..::--""_(##)#)"':. \ \)    
    /_:-:'/  :__(##)##)    ): )   
    "  / |  :' :/""\///)  /:.'  
      / :( :( :(   (#//)  "       
     / :/|\ :\_:\   \#//\   
     |:/ | ""--':\   (#//)              
     \/  \ :|  \ :\  (#//)
          \:\   '.':. \#//\      
           ':|    "--'(#///)
                      (#///)
                      (#///)
                       \#///\
                       (##///)
                       (##///)
                       (##///)
                       (##///)
                        \##///\
                        (ANV///)
                        (IRV///)
                        (MWV////)__...-----....__
                        (#/::'''                 ""--.._
                   __..-'''                             "-._
           __..--""           By BrianV1981            	   "-..____
  ___..--""                                                    "-..____
    (_ ""---....___                                     __...--"" _)
      """--...  ___"""""-----......._______......----"""     --"""
                    """"       ---.....   ___....----

## <details>
  <summary>Overview</summary>

  The `arma3mercenaries Enhanced Kill Script` provides comprehensive features for managing kill notifications (killfeed), rewards, penalties, and death markers in Arma 3 missions. The script supports a wide range of customizable options via CBA (Community Base Addons), enabling players and mission creators to tailor the experience to their needs.

</details>

## <details>
  <summary>Core Features</summary>

### **Killfeed Notification**
- **Description**: Displays a HUD notification for every kill, showing the name and distance of the killed unit.
- **CBA Settings**:
  - **Enable Killfeed**: Toggles the display of the killfeed notification.
  - **Killfeed Display Duration**: Adjusts the duration (in seconds) that the killfeed notification remains on screen.
  - **Enable Kill Notification Sound**: Toggles the sound notification that plays when a kill is registered.

### **Rewards and Penalties**
- **Friendly Fire Penalty**:
  - **Description**: Deducts a specified amount of credits from the player’s bank account for friendly fire incidents.
  - **CBA Settings**:
    - **Friendly Fire Penalty (Bank)**: Sets the amount of credits deducted for friendly fire incidents.
- **Friendly Fire Compensation**:
  - **Description**: Awards a specified amount of credits to a player killed by friendly fire. Credits are added to the player’s bank account.
  - **CBA Settings**:
    - **Friendly Fire Compensation (Bank)**: Sets the amount of credits awarded to a player when killed by friendly fire.
- **Kill Rewards**:
  - **Description**: Awards a random amount of credits to the killer for killing enemy units.
  - **CBA Settings**:
    - **OPFOR Kill Reward (Random, Wallet)**: Sets the maximum random amount of credits awarded for killing an OPFOR unit.
    - **NATO Kill Reward (Random, Wallet)**: Sets the maximum random amount of credits awarded for killing a NATO unit.
    - **Independent Kill Reward (Random, Wallet)**: Sets the maximum random amount of credits awarded for killing an Independent unit.
- **Kill Penalties**:
  - **Description**: Deducts a specified amount of credits from the killer’s bank account for killing certain units, such as civilians or allied Independents.
  - **CBA Settings**:
    - **NATO Penalty for Killing Independent (Bank)**: Sets the amount of credits deducted for killing an Independent unit as NATO.
    - **Civilian Kill Penalty (Bank)**: Sets the amount of credits deducted for killing a civilian.

### **AI Wallet Management**
- **Description**: Adds a random amount of credits to the wallets of killed AI units, making them lootable.
- **CBA Settings**:
  - **OPFOR AI Wallet Amount (Random, Wallet)**: Sets the maximum random amount of credits found on a killed OPFOR AI unit.
  - **NATO AI Wallet Amount (Random, Wallet)**: Sets the maximum random amount of credits found on a killed NATO AI unit.
  - **Independent AI Wallet Amount (Random, Wallet)**: Sets the maximum random amount of credits found on a killed Independent AI unit.
  - **Civilian AI Wallet Amount (Random, Wallet)**: Sets the maximum random amount of credits found on a killed Civilian AI unit.

### **Death Markers**
- **Description**: Creates markers on the map at the location where a player or AI unit was killed. The marker includes the faction, killer’s name, weapon used, and the distance.
- **CBA Settings**:
  - **Death Marker Size**: Sets the size of the death markers on the map.

### **Death Penalty**
- **Description**: Deducts a specified amount of credits from the player's bank account upon death.
- **CBA Settings**:
  - **Death Penalty Amount (Bank)**: Sets the amount of credits deducted when the player dies.

### **Silent Hints**
- **Description**: Provides notifications related to rewards and penalties without disrupting gameplay with loud hints.
- **CBA Settings**:
  - **Enable Silent Hints**: Toggles the display of silent hints related to kill rewards and penalties.

</details>

## <details>
  <summary>In-Game Experience</summary>

- **Immersive Feedback**: Players receive immediate visual and audio feedback for their kills and deaths, enhancing the tactical experience.
- **Customization**: With the extensive CBA settings, mission creators and players can fine-tune how the script interacts with their gameplay, including adjusting rewards, penalties, killfeed behavior, and more.

</details>

## <details>
  <summary>Usage</summary>

To integrate and use this script in your mission, simply add the script files to your main mission folder and ensure the CBA settings are configured to your preference.

</details>

## <details>
  <summary>Script Summary</summary>

### Overview

This script manages:

* **Killfeed notifications**
* **Rewards and penalties**
* **Death markers**

It applies to both **AI** and **player-controlled units** in an **Arma 3 mission**. The script handles various scenarios based on the **faction of the killed unit** and applies appropriate rewards or penalties. It also creates markers on the map to indicate where a player or AI unit was killed, enhancing the tactical experience of the mission.

### Core Logic Breakdown

#### 1. Local Instigator Check
* The script verifies if the **_instigator** (the unit responsible for the kill) is local to the machine, ensuring only relevant scenarios are processed.
* It checks if the killed unit is a **human-like entity** (`CAManBase`), limiting the script's application to appropriate scenarios.

#### 2. Determine Sides of Killer and Killed Unit
* The script determines the **faction** (side) of both the killer and the killed unit by checking their configuration in the game.
* These values are stored in **_sideKiller** and **_sideKilled**.

#### 3. Determine Name and Color of Killed Unit
* The script retrieves the **name and color** associated with the killed unit.
  * For AI units, it uses the **display name** from the game’s configuration.
  * For player units, it uses the **player’s in-game name**.
* The color of the unit is determined based on their faction and stored in **_killed_Color**.

#### 4. Calculate Distance Between Killer and Killed Unit
* The script calculates the **distance** between the killer and the killed unit, storing this value in **_distance**.

#### 5. Retrieve Weapon Information
* The weapon used for the kill is identified, and its **display name** is retrieved from the game’s configuration.
* If no weapon picture is available, the script checks for the **vehicle used** by the instigator.

#### 6. Friendly Fire Detection
* If the killer and the killed unit belong to the **same faction** (friendly fire) and the killer is a player:
  1. The script **deducts 10,000 credits** from the player’s bank account as a penalty.
  1. A **hint** is sent to the player informing them of the friendly fire incident and the penalty.
  1. If a player is killed by friendly fire, they receive **20,000 credits** to their bank account (10,000 to offset the death penalty and 10,000 as compensation). A hint is sent to the player with details about the incident.

#### 7. Side-Based Reward and Penalty Logic

##### Case 0: OPFOR Killed
* **Reward**: The killer (player or AI) receives a random reward of up to **10,000 credits** added to their wallet. If the killer is a player, they receive an on-screen hint about the reward.
* **Additional Feature**: The killed OPFOR unit receives a random amount of up to **10,000 credits** in their wallet, making their corpse lootable.
* **Killfeed**: A **HUD notification** displays the name and distance of the killed OPFOR unit.
* **Death Marker**: If a player kills an OPFOR AI unit, a **red death marker** is placed on the map at the location of the kill, labeled with the faction name, killer’s name, weapon used, and the distance.

##### Case 1: NATO Killed
* **Reward/Penalty**: If the killer is OPFOR, they receive a reward of up to **10,000 credits** added to their wallet. If the killer is NATO (friendly fire), they are penalized with a **10,000 credit deduction** from their bank account, and a hint is shown.
* **Additional Feature**: The killed NATO unit receives a random amount of up to **1,000 credits** in their wallet.
* **Killfeed**: A **HUD notification** displays the kill information.
* **Death Marker**: If a player kills a NATO AI unit, a **blue death marker** is placed on the map, labeled with the faction name, killer’s name, weapon used, and the distance.

##### Case 2: Independent Killed
* **Reward/Penalty**: If the killer is OPFOR, they receive a reward of up to **10,000 credits** added to their wallet. If the killer is NATO (NATO allied), they are penalized with a **10,000 credit deduction** from their bank account, and a hint is shown.
* **Additional Feature**: The killed Independent unit receives a random amount of up to **1,000 credits** in their wallet.
* **Killfeed**: A **HUD notification** displays the kill information.
* **Death Marker**: If a player kills an Independent AI unit, a **green death marker** is placed on the map, labeled with the faction name, killer’s name, weapon used, and the distance.

##### Case 3: Civilian Killed
* **Penalty**: The killer, regardless of side, is penalized with a **10,000 credit deduction** from their bank account, and a hint is shown.
* **Additional Feature**: The killed Civilian unit receives a random amount of up to **1,000 credits** in their wallet.
* **Killfeed**: A **HUD notification** displays the kill information.
* **Death Marker**: If a player kills a Civilian AI unit, a **purple death marker** is placed on the map, labeled with the faction name, killer’s name, weapon used, and the distance.

</details>

## <details>
  <summary>Additional Features</summary>

### **Killfeed HUD Notification**
- A visual **HUD notification** is displayed for every kill, showing the name and distance of the killed unit.

### **Sound Notification**
- A **sound** is played whenever a kill is registered.

### **AI Death Marker**
- A **death marker** is placed on the map for the last AI unit killed by a player. The marker’s color corresponds to the side of the killed unit, and the label includes the faction name, killer’s name, weapon used, and distance.

### **Player Death Marker**
- If a player is killed, a **red warning marker** is placed on the map at their death location, displaying the player’s name.

### **Death Penalty**
- If a player dies, they receive a **financial penalty** of 10,000 credits deducted from their bank account, and a hint is displayed informing them of the deduction.

</details>

## <details>
  <summary>In-Game Experience</summary>

* **Rewards and Penalties**: Players and AI units receive **financial rewards** or **penalties** based on their actions, such as killing enemy units, committing friendly fire, or killing civilians.
* **Killfeed**: Players receive **immediate visual feedback** about their kills through HUD notifications, enhancing the gameplay experience.
* **Death Markers**: Markers placed on the map provide visual cues for the locations of recent kills, helping players track significant events during the mission.
* **Death Penalty**: Players face **financial consequences** for dying, encouraging more careful and strategic gameplay.

</details>

## <details>
  <summary>Conclusion</summary>

This comprehensive system is designed to enhance the tactical and immersive aspects of **arma3mercenaries missions** by rewarding or penalizing actions based on faction dynamics while also providing players with clear and immediate feedback through visual and audio notifications.

</details>
