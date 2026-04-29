# How to make an Orbital Strike Cannon Stab Shot with just command blocks

Ever wanted that cool Orbital Strike Cannon Stab Shot fishing rod that pratically stabbed into the ground with tnt, destroying almost anything in its path? But you're too lazy to build a huge redstone contraption for that? Well you have come to the right place! Now you can recreate it with just 38 command blocks and one chat command! (This has raycasting and everything. Make sure you have a beefy computer.)

---
First, run this command in the chat:

```
/scoreboard objectives add useStabShot minecraft.used:fishing_rod
```

---
Next, place down an impulse (needs redstone, unconditional) command block containing this command:

```
give @p minecraft:fishing_rod[item_name="Stab Shot",custom_data={isStabShot:1b}]
```

Place a button on this command block and press it to give yourself the special fishing rod you will need to blow stuff up.

---
Next, anywhere, place down a repeating (always active, unconditional) command block with this command:

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] at @s anchored eyes unless entity @e[type=minecraft:armor_stand,tag=stabShotRay] run summon armor_stand ~ ~1.5 ~ {Invisible:1b,Marker:1b,Tags:["stabShotRay"]}
```

This command checks if you are holding and have used the special fishing rod and spawns an invisible armor stand for the raycasting sequence.

---
Next to that repeating command block, place a chain (always active, unconditional) command block and then another next to that one and so on until you have one for every command in this list. Then place these commands one at a time in each command block. For each command in the list, I will say what it does below it. (However, because of the absurd amount of commands that are below, I just had AI explain each of them. If an explaination sounds like it was translated in Google Translate a thousand times, then too bad.)

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run data modify entity @e[tag=stabShotRay,tag=!stabShotRayAligned,limit=1] Rotation set from entity @s Rotation
```
> This command runs as any player currently using the stab shot rod and makes the raycasting armor stand copy the player’s exact facing direction. It finds the armor stand that hasn’t been aligned yet and sets its rotation to match the player, so the raycast will travel exactly where the player is looking.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run tag @e[type=minecraft:armor_stand,tag=stabShotRay,tag=!stabShotRayAligned] add stabShotRayAligned
```
> This command tags the raycasting armor stand as “aligned” after its rotation has been set. This prevents the rotation from being constantly overwritten every tick and ensures the ray keeps moving in a consistent direction after being aimed.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[tag=stabShotRay] at @s if block ~ ~ ~ minecraft:air run tp @s ^ ^ ^10
```
> This command moves the raycasting armor stand forward by 10 blocks in the direction it is facing, but only if it is currently inside air. This is one of the main steps of the raycasting system, allowing the ray to travel forward through empty space.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-10 air run tag @s add stabShotHit
```
> This command checks 10 blocks behind the armor stand (back along the ray path) to see if there is a solid block instead of air. If there is, it tags the armor stand as having hit something. This is part of detecting where the ray intersects with terrain.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-10 air run tp @s ^ ^ ^-10
```
> This command moves the armor stand backward by 10 blocks if a solid block is detected behind it. This helps reposition the ray to the exact surface where it collided instead of staying inside or beyond the block.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-9 air run tag @s add stabShotHit
```
> This command checks slightly closer positions behind the armor stand (in this case 9 blocks back) to refine where the collision happened. If a solid block is found, it marks the ray as having hit something.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-9 air run tp @s ^ ^ ^-9
```
> This command moves the armor stand to that exact closer position when a solid block is found. Together with the previous command, this creates a step-by-step refinement process that finds the exact surface of the block the player aimed at.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-8 air run tag @s add stabShotHit
```
> This command checks slightly closer positions behind the armor stand (in this case 8 blocks back) to refine where the collision happened. If a solid block is found, it marks the ray as having hit something.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-8 air run tp @s ^ ^ ^-8
```
> This command moves the armor stand to that exact closer position when a solid block is found. Together with the previous command, this creates a step-by-step refinement process that finds the exact surface of the block the player aimed at.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-7 air run tag @s add stabShotHit
```
> This command checks slightly closer positions behind the armor stand (in this case 7 blocks back) to refine where the collision happened. If a solid block is found, it marks the ray as having hit something.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-7 air run tp @s ^ ^ ^-7
```
> This command moves the armor stand to that exact closer position when a solid block is found. Together with the previous command, this creates a step-by-step refinement process that finds the exact surface of the block the player aimed at.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-6 air run tag @s add stabShotHit
```
> This command checks slightly closer positions behind the armor stand (in this case 6 blocks back) to refine where the collision happened. If a solid block is found, it marks the ray as having hit something.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-6 air run tp @s ^ ^ ^-6
```
> This command moves the armor stand to that exact closer position when a solid block is found. Together with the previous command, this creates a step-by-step refinement process that finds the exact surface of the block the player aimed at.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-5 air run tag @s add stabShotHit
```
> This command checks slightly closer positions behind the armor stand (in this case 5 blocks back) to refine where the collision happened. If a solid block is found, it marks the ray as having hit something.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-5 air run tp @s ^ ^ ^-5
```
> This command moves the armor stand to that exact closer position when a solid block is found. Together with the previous command, this creates a step-by-step refinement process that finds the exact surface of the block the player aimed at.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-4 air run tag @s add stabShotHit
```
> This command checks slightly closer positions behind the armor stand (in this case 4 blocks back) to refine where the collision happened. If a solid block is found, it marks the ray as having hit something.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-4 air run tp @s ^ ^ ^-4
```
> This command moves the armor stand to that exact closer position when a solid block is found. Together with the previous command, this creates a step-by-step refinement process that finds the exact surface of the block the player aimed at.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-3 air run tag @s add stabShotHit
```
> This command checks slightly closer positions behind the armor stand (in this case 3 blocks back) to refine where the collision happened. If a solid block is found, it marks the ray as having hit something.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-3 air run tp @s ^ ^ ^-3
```
> This command moves the armor stand to that exact closer position when a solid block is found. Together with the previous command, this creates a step-by-step refinement process that finds the exact surface of the block the player aimed at.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-2 air run tag @s add stabShotHit
```
> This command checks slightly closer positions behind the armor stand (in this case 2 blocks back) to refine where the collision happened. If a solid block is found, it marks the ray as having hit something.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-2 air run tp @s ^ ^ ^-2
```
> This command moves the armor stand to that exact closer position when a solid block is found. Together with the previous command, this creates a step-by-step refinement process that finds the exact surface of the block the player aimed at.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-1 air run tag @s add stabShotHit
```
> This command checks slightly closer positions behind the armor stand (in this case 1 block back) to refine where the collision happened. If a solid block is found, it marks the ray as having hit something.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-1 air run tp @s ^ ^ ^-1
```
> This command moves the armor stand to that exact closer position when a solid block is found. Together with the previous command, this creates a step-by-step refinement process that finds the exact surface of the block the player aimed at.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ~ ~ ~ air run tag @s add stabShotHit
```
> This final check looks at the armor stand’s current position and, if it is no longer in air, confirms the hit by tagging it. This acts as the final confirmation that the raycast has reached a solid surface.
```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] run tag @e[type=minecraft:experience_orb] add b4
```
> This command tags all experience orbs with ```b4``` whenever a hit is detected. This is used to mark existing orbs so the system can tell which ones are newly created later.
```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] at @s run summon minecraft:experience_orb
```
> This command summons a new experience orb at the hit location. The orb is used as a temporary reference point for later commands, helping position other entities precisely.
```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] at @e[type=minecraft:experience_orb,tag=!b4] run summon minecraft:armor_stand ~ ~1000 ~ {Rotation:[0f,90f],Marker:1b,Tags:["stabShotMarker"],Invisible:1b}
```
> This command finds the newly created experience orb and spawns an invisible marker armor stand 1000 blocks above it with a specific rotation. This marker is used to define direction and positioning for the upcoming strike pattern.
```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] at @e[type=minecraft:experience_orb,tag=!b4] run summon minecraft:armor_stand ~ ~1000 ~ {Rotation:[0f,-90f],Marker:1b,Tags:["stabShotMarker"],Invisible:1b}
```
> This command does the same as the previous one but with the opposite rotation. Having two markers with different rotations allows the system to create a symmetrical or directional spread for the strike.
```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] as @e[type=minecraft:experience_orb,tag=!b4] at @s rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^4 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-2 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-4 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-8 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-16 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-32 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-64 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-128 run summon minecraft:end_crystal ~ ~ ~ {ShowBottom:0f,Tags:["stabShotCrystal"],Passengers:[{id:"minecraft:end_crystal",ShowBottom:0f,Tags:["stabShotCrystal"]}]}
```
> This command uses the experience orb and the marker armor stands to repeatedly rotate and shift position in different directions, building a long chain of positions extending outward. At the final position, it summons end crystals (including one riding another), which will later be used as the exact points where TNT is spawned. This is what creates the long, directional “stab” line in the sky.
```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] at @e[type=minecraft:experience_orb,tag=!b4] positioned ~ ~1000 ~ run kill @e[type=minecraft:armor_stand,tag=stabShotMarker,distance=..5]
```
> This command removes the temporary marker armor stands near the high-altitude position after they have been used. It cleans up unnecessary entities to prevent buildup and lag.
```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] at @e[type=end_crystal,tag=stabShotCrystal] run summon tnt ~ ~ ~ {fuse:0,NoGravity:1b}
```
> This command summons TNT at every end crystal location with no gravity and an instant fuse. This creates the actual orbital strike explosions exactly along the positions calculated earlier.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] if entity @e[type=minecraft:armor_stand,tag=stabShotHit] run kill @e[type=minecraft:armor_stand,tag=stabShotHit]
```
> This command removes the armor stand that marked the hit after the strike has been triggered. This ensures the system resets properly and doesn’t reuse the same hit point.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] unless entity @e[type=minecraft:armor_stand,tag=stabShotRay] run scoreboard players set @s useStabShot 0
```
> This command resets the player’s ```useStabShot``` score if no raycasting armor stand exists anymore. This effectively ends the firing process and prepares the system for the next use.
```
execute as @a unless entity @s[scores={useStabShot=1..}] run kill @e[type=minecraft:armor_stand,tag=stabShotRay]
```
> This command removes all raycasting armor stands for players who are no longer using the stab shot. It prevents leftover entities from staying in the world.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] if entity @e[type=minecraft:armor_stand,tag=stabShotRay,distance=200..] run scoreboard players set @s useStabShot 0
```
> This command checks if the raycasting armor stand has gone too far away (more than 200 blocks). If it has, it stops the system by resetting the player’s score, preventing runaway raycasts.
```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run kill @e[type=minecraft:armor_stand,tag=stabShotRay,distance=200..]
```
> This command removes any raycasting armor stands that are too far away from the player. This acts as a cleanup and safety measure to keep the system efficient and controlled.
