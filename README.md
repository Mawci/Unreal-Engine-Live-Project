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

# *Please note this summary has been migrated into a full [portfolio](https://mawci.github.io)*

## User Stories
 * Story 1 [Landscape and Structures](#landscape-and-structures)
   * [Terrain](#terrain)
   * [Assets](#assets)
   * [Foliage](#foliage)  
 * Story 2 [GameMode and HUD](#gamemode-and-hud)
   * [Character Animations](#character-animations)
   * [Shooting](#shooting)
 * Story 3 [Collectables / Obstacles](#collectables-obstacles)
 * Story 4 [Menu](#environment)
 * Story 5 [Complete Gameplay](#animations)
 * Story 6 [Sound](#enemies)

 * [Skills](#other-skills-learned)

##

### Landscape and Structures

&emsp;In this story I was responsible for creating a level for the game. The description of the story stated, *"playable area doesn't need to be big, but should allow for at least a few structures."*  

#### <p align="center">Terrain</p>
With this in mind, I started learning the landscaping tool to create the terrain of the level. I learned about the masks to use in the modeler and broke up the level with mountains in the background and some uneven slopes in the playable area. I wanted to keep the playable area relatively flat as I wanted to have enemies chasing the character and was unsure how it might impact their navigation. The first problem I ran into was when I added a ground texture to the terrain, it looked extremely unnatural. When the texture repeated, it resembled something similar to thousands of minecraft blocks. I was able to solve this when I found a guide on learn.unrealengine that talked about reference materials. By editing the scale of the reference material for the ground texture, I was able to make the terrain look natural without any indication of repetition.
 
#### <p align="center">Assets</p>
Next, I began importing assets and learned the workflow from Fab, Cosmos, and Sketchfab3d. Most of the assets used in this game came from Fab. This is an example where I had to teach myself as Unreal Engine had just migrated all of its Marketplace and Quixel bridge into it. Every guide and forum I found on the internet referencing asset integration were using the deprecated methods whereas everything I found written about Fab seemed to be nothing more than marketing and launch hype. I'm hopeful the kinks will get straightened out in the future but through using Fab during this project, I experienced many bugs, loss of content that was originally in my marketplace, numerous crashes, and lag.

A few lessons learned:
* Save the project before opening Fab
* If importing more than one asset at a time it is better to import it to a blank project and migrate the asset to your working environment
* Close out of Fab and restart Unreal Engine after importing
* If importing assets from the same publisher at different times, you may need to manually rename the folder the assets are in or the new ones will not show up 

Every asset imported had collision boxes that were not representative of the meshes.  I therefore went through each asset, removing the default collision and customizing it.

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/mutipleColliders.png" width="600" width="338" />
</p>

In some situations like  with the fence assets below,  I increased  the collisions to ensure the player couldn't escape the boundary of the map by jumping over it.

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/customCollision.png" width="600" width="338" />
</p>

After collision editing, I built a small area resembling a ghost town that the player could walk around in, as you can see below. Also notice how the repeating texture of the ground seems unnoticeable and natural. 

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/environment.png" width="600" width="338" />
</p>

#### <p align="center">Foliage</p>
To complete this story, I utilized the foliage mode in the editor to add some life. Customizing the active brush size and density ensured different variations of fields or plant types, helping to break up the scene with an added sense of immersion.

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/foliageMode.png" width="600" width="338" /></p>


<!--
![](https://github.com/Mawci/Live-Project-Unity/blob/main/Gifs/loadScreen-ezgif.com-video-to-gif-converter.gif)
-->




*Jump To: [Page Top](#introduction), [Player Abilites](#player-abilities), [Environment](#environment), [Animations](#animations), [Enemies](#enemies), [New Level](#new-level), [Game Over](#game-over), [Skills](#other-skills-learned)*
##

### Gamemode and HUD 

&emsp;This story had a description of, *"set up your GameMode and create a Heads Up Display. The GameMode will dictate how the level will function as well as the default pawn that will spawn when the level loads."* I first prioritized these minimum deliverables by adding the 3rd person gamemode to the level settings, changing the default pawn to the 3rd person character blueprint, and creating a widget blueprint that had placeholders for ammo and health. This ensured that I completed what was expected so that I could develop further functionality without fear of falling behind schedule or delaying completion. 
<br/> <br/>
#### <p align="center">Character Animations</p>
&emsp;There were countless ideas that came to mind to build out this gamemode, each one more creative and fun than the last, but I knew how to implement none of them. In an attempt to break down the overwhelming mountain of information I had to learn, I started with the most basic thing I could think of. Character animations. Make the character look like they're holding a gun. This was a small enough step for me to break down into something actionable. I imported a free animation pack from Fab, retargeted the animations for the current version of Unreal Engine’s mannequin, and started building out a blendspace for the character. 

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/BlendSpace.png" width="600" width="338" />
</p>


This worked, but I wanted to utilize walking/running animations for the bottom half of the character while the character's arms continued to hold a rifle. After looking up how this can be achieved, I created a separate blendspace so that the character now had independant upper and lower body animation. Then in the animation blueprint, as you can see below, I was able to combine the two animations by use of the “layered blend per bone” node implementing it from the spine_03 bone downwards.
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/layeredblendBone.png" width="600" width="338" />
</p>

With the animations set, I then learned that meshes can be attached to other meshes by use of sockets. By adding a socket to the character’s skeleton mesh as seen below, I was able to then add a weapon mesh and adjust the rotation to make it seem like it is being held.

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/addingWeapon2Socket.gif" />
</p>

With just the additions of animation blending and rifle holding, the game was already starting to feel like a shooter. 

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/locomotion.gif" />
</p>

#### <p align="center">Shooting</p>
&emsp;Next was getting the weapon to shoot. My goal was to simply show a flash indicating the weapon had been fired when the player hit the left mouse button. I wanted to have control over where that flash would be located, so learning off of what I did previously, I added a socket to the rifle mesh on the barrel. My plan was to access the mesh, get the location of the socket, and spawn in a particle effect.
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/linetracesocket.png" width="600" width="338" />
</p>

&emsp;I soon learned this implementation was problematic as the player should not be responsible for spawning in the particles for the weapon object. That’s because if I wanted to expand on the weapons behavior (like adding sound effects or more particles) I would always need to go into the character blueprint to update it– leading to an extensibility nightmare. I read that it is better practice for the object to handle all responsibilities pertaining to it. A common way of doing that is by playing an animation with event notifies. Therefore I recorded a new animation sequence of the weapon to represent firing, with added notifications for sound and vfx.  

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/weaponfiringanimation.gif"  /> 
</p>

&emsp;The next functionality I needed to learn was actually making the weapon shoot. There were a couple ways of doing this but I implemented a line trace projected from the bullet’s muzzle socket to where the player is looking. To do this, I simply called the animation of the weapon firing when the left mouse button was held and called a line trace. If the left mouse button. I then had a branch checking if the button was still held to continue shooting. Below you can see a snapshot of the shoot function calling the fire animation and an animation that adds recoil to the character. 

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/weaponShootScreenshot.png"  />
</p>

<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/images/LineTraceScreenShot.png"  />
</p>

&emsp;Above is the implementation of the line trace when called by the shoot function. Notice how I added different random variations to the end location of the trace depending on the player aiming or hip firing. I realize there are many more sophisticated ways to implement a bullet spread system, but this was quick and served its purpose for incentivising the player to aim to be more accurate. This was also and area I had to return to after playtesting. Since I initially had the start position of the line trace at the muzzle of the gun, there would be many situations where traces towards closer objects would hit without the crosshairs being over it. This wasn't telegraphed well to the player and I personally found it frustrating when missing enemies because they were too close to me. To fix this I calculated the center point of the screen and projected it to world space for the start position. With that, the trace would always hit what the crosshair was hovered over, eliminating any discrepancies.


&emsp;By the end of this story, I had a complete shooting functionality and animations for moving around the level. You can see below the difference in variations for the line traces depending on aiming or hip firing.
<p align=center>
    <img src="https://github.com/Mawci/Unreal-Engine-Live-Project/blob/main/gifs/shootTestingwithspread.gif" />
</p>



*Jump To: [Page Top](#introduction), [Game Scenes](#game-scenes), [Environment](#environment), [Animations](#animations), [Enemies](#enemies), [New Level](#new-level), [Game Over](#game-over), [Skills](#other-skills-learned)*

##

###  Collectables Obstacles


&emsp; *"This story will be completed when you have collectables that update your HUD when collected and obstacles throughout your level"*
<br/>
<br/>


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

### Enemy

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
