# Live Project
## Introduction
&emsp;This project was done as an apprenticeship for [Prosper IT Consulting](https://www.linkedin.com/company/prosper-it-consulting/) where I participated in Agile/Scrum practices by completing user stories (as well as sprint planning, daily stand-ups, sprint retrospective) to deliver a functional MVP game in Unreal Engine version 5.3. I was fully responsible for every aspect of the game's development including concept, planning, design, animation, and programming. I attempted an extremely ambitious feat of creating a 3rd Person Shooter Survival game that would be both "fun" and replayable. Since this was my first game created using Unreal Engine, nearly every feature/mechanic included had to be referenced from Unreal's documentation, forums, or tutorial guides. I fully committed myself during the 2 week sprint, working 10+ hour days including weekends to achieve this success. There were many times throughout development were I learned better ways of implementing features or improving efficiencies, but I wasn't able to incorporate all of them for the sake of time. This is just a disclaimer that the project is nowhere near perfect and many times I just needed to get something working to move forward.  Completing this game, however, taught me better development [skills](#other-skills-learned) which I will continue building upon in future projects.
##
<br>
<p align="center">
  If you would like to play the game, it is currently pending publication but can be downloaded 
  <a href="https://drive.google.com/file/d/1IN401tqY5BuFzRkgJjavJWHKRzgLT6Fq/view?usp=drive_link">here</a>.
</p>

<p align=center>
<img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/trailer.gif" frameborder="0" allowfullscreen="true" scrolling="no" height="378" width="620"/>
</p>


&emsp;Below are descriptions of the stories I worked on, screenshots, gifs, and navigation links. I have also included all the .uassets of blueprints created for the game in this repository. If there are any details not included in this summary that you would like to know about, please feel free to contact me.

## User Stories
 * Story 1 [Landscape and Structures](#landscape-and-structures)
 * Story 2 [GameMode and HUD](#player-movement)
   * [Character Animations]()
   * [Weapon Animations]()
   * [Wepon Shooting]()
   * [Shooting Logic]()
 * Story 3 [Collectibles / Obstacles](#player-abilities)
 * Story 4 [Menu](#environment)
 * Story 5 [Complete Gameplay](#animations)
 * Story 6 [Sound](#enemies)

 * [Skills](#other-skills-learned)

##

### Landscape and Structures


&emsp; In this story I was responsible for creating a level for the game. The  playable area doesn't need to be big, but should allow for at least a few structures.  


^Description
started with the landscaping tool to create the terrain of the level. ran into a problem with the materials looking extremely unnatural and refrence the material instance to change the scale of the tile and now the dirt and terrain look natural. 
next imported assets and learned the workflow from Fab, Cosmos, and Sketchfab3d. I had to explore myself on this as Unreal Engine had just migrated all of its Marketplace and Quixel bridge into Fab.
Many of the imported assets had terrible collision boxes that were not representabive of the meshes. I there for went through every imported asset, removing the collision and adding custom collision to each on. I did this knowing that the player would be relying on every bit of real estate in the map to avoid being killed and it would only lead to frustration for the player being blocked by invisible walls. I also increase some collision boxes like the one you see below to ensure the player stayed within the boundary of the map, this was after discovering the player could strafe jump ontop of the fence.

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/customCollision.png" width="600" width="338" /></p>
With all of the asset collision boxes edited, I built a small area the player could walk aroun in. Started out as you can see below. 
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/environment.png" width="600" width="338" /></p>
trees and foliage were added afterwards with use of the foliage mode editor in unreal engine. customizing the active brush size and density ensure variations in certain types of plants that helped to break up the scene and add a feeling of immersion. 
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/foliageMode.png" width="600" width="338" /></p>


<!--
![](https://github.com/Mawci/Live-Project-Unity/blob/main/Gifs/loadScreen-ezgif.com-video-to-gif-converter.gif)
-->




*Jump To: [Page Top](#introduction), [Player Abilites](#player-abilities), [Environment](#environment), [Animations](#animations), [Enemies](#enemies), [New Level](#new-level), [Game Over](#game-over), [Skills](#other-skills-learned)*
##

### Player Movement

&emsp;This story was seemingly simple as the movement in Space Invaders is not too complex, however I still ran into a bug that I needed to carefully step through. Initially, I used transform.Translate() to move the player using its horizontal vector multipied by a constant speed. This worked, but I needed a way to ensure the player stayed within the viewable bounds of the screen. To solve this, I created two variables that would hold the maximum position on the right and left sides of the screen before going out of view. Then I did a simple check to see if the player was within those two values. If they were, then allow input to move the player.
<br/> <br/>
retargeted the animations using unreals retargeter and then created a blendspace
created 2 different blendspaces for the character animation blueprint based on the speed. I set the max speed knowing that I would need to be faster than the max speed of the enemies. Below you can see the 
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/BlendSpace.png" width="600" width="338" />
</p>

with the blendspace created I then blended them in the animation blueprint to combine the lower anims of the locomotions with the uper anims of holding a rifle
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/layeredblendBone.png" width="600" width="338" />
</p>

with the animation set, now I learned how to attach object to skeleton meshes by creating sockets. i created a right hand socket on the bone of the right hand and added the weapon skeleton mesh to the socket of the character mesh. Then minor adjustments to the rotation of the weapon made the weapon holding animation look more realistic.
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/addingWeapon2Socket.gif" />
</p>
The combination of the blending and weapon in the socket started to make the game feel like a shooter. Below you can see the first stages of the character moving with just those few additions. 
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/locomotion.gif" />
</p>

SHOOTING
Next was getting the weapon to shoot. I edited the skeleton mesh of the weapon to add a socket similarly. This was so I would have a place to add particle animations and intially I did my debug lines from this when shooting. (later I found out that it felt to unnatural and I need to change the starting position of the line trace.
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/linetracesocket.png" width="600" width="338" />
</p>

I created my own anaimation sequence by recording the weapon not moving. This was perfect bc all the animations of the gun were only going to be the it flashing. I learned about animation notifies and below I added a notify to spawn a particle during the shoot animation. It was only the starter content explosion for a placeholder until I later imported a muzzleflash effect, but it served its purpose.  
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/weaponfiringanimation.gif"  /> 
</p>


<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/LineTraceScreenShot.png" width="600" width="338" />
</p>

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/weaponShootScreenshot.png" width="600" width="338" />
</p>


<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/shootTestingwithspread.gif" />
</p>


<p align=center>
    <img src="" />
</p>


*Jump To: [Page Top](#introduction), [Game Scenes](#game-scenes), [Environment](#environment), [Animations](#animations), [Enemies](#enemies), [New Level](#new-level), [Game Over](#game-over), [Skills](#other-skills-learned)*

##

### Player Abilities Collectables Obstacles


&emsp;For this story 
<br/>
<br/>
### Interactable Objects 

using interfaces
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/skullPickup.png" width="600" width="338" />
</p>

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/skullPickupOnOverlapCheck.png" width="600" width="338" />
</p>

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/buyableCollisionBox.png" width="600" width="338"/>
</p>


<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/buyableOverlapEvent.png" width="600" width="338"/>
</p>

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/overlapInteractable.gif" />
</p>

<p align=center>
    <img src=" https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/tierableUpgradeLogic.png" width="600" width="338" />
</p>


    



### Updating the HUD based on the state of the game

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/HUD%20BINDINGS.png" width="600" width="338"/>
</p>

###Enemy

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/animationBlending.png" width="600" width="338"/>
</p>

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/physicsEditing.png" width="600" width="338"/>
</p>

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/enemyhitdetection.gif" />
</p>




<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/EnemyAttackwithArrowComp.png" width="600" width="338"/>
</p>

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/enemyAttacking.gif" />
</p>


*Jump To: [Page Top](#introduction), [Game Scenes](#game-scenes), [Player Movement](#player-movement), [Animations](#animations), [Enemies](#enemies), [New Level](#new-level), [Game Over](#game-over), [Skills](#other-skills-learned)*
##

### Environment


&emsp;In this story I began by implementing 



<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/titleScreen.png" />
</p>


<!-- ###### <p align="center"> The reset you see above is actually the video recording reset!<br/> The reset of the background happens here without you noticing.<br/> Try [playing the game](https://play.unity.com/en/games/1e29f742-4101-4814-abab-023970facbcd/space-invaders-clone) to see how seamless it is.</p><br/>
-->



## Other Skills Learned

* Gained practical experience collaborating with a team of developers in a Scrum environment, participating in sprint planning, retrospectives, and daily stand-ups to enhance project efficiency.
* Demonstrated adaptability by seamlessly integrating into ongoing development, quickly mastering custom naming conventions and workflows for Azure DevOps, and utilizing Git for version control.
* Proactively identified potential issues before they escalated, [communicating](#communicating-early) effectively with the project manager to prevent downtime and ensure smooth development processes.
* Actively communicated with team members, providing support in problem-solving during stand-up meetings. For example, I assisted a fellow developer in troubleshooting 2D collision detection, resulting in a faster resolution.
* Ability to research and learn material that I am unfamiliar with. Several examples throughout this project where I needed to reference the Unity documentation to successfully implement features.
  * [Animation events](#explosion-particle-bug)
  * [New Font Assets](#game-scenes)
  * [Parallax Background](#environment)
  * [Persistent Data](#game-over)
* Gained hands-on experience in debugging by systematically identifying and resolving errors, fostering a deeper understanding of the development process and enhancing my problem-solving abilities.
  * [Input Bug](#movement-bug)
  * [Bullet Spamming](#bullet-spamming-bug)
  * [Shield Error](#shield-error)
  * [Explosion Particle](#explosion-particle-bug)
  * [Wave Error](#enemy-wave-error)

*Jump To: [Page Top](#introduction), [Game Scenes](#game-scenes), [Player Movement](#player-movement), [Player Abilites](#player-abilities), [Environment](#environment), [Animations](#animations), [Enemies](#enemies), [New Level](#new-level)*
