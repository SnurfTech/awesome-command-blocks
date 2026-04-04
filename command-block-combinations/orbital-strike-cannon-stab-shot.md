# How to make an Orbital Strike Cannon Stab Shot with just command blocks

Ever wanted that cool Orbital Strike Cannon Stab Shot fishing rod that pratically stabbed into the ground with tnt, destroying almost anything in its path? But you're too lazy to build a huge redstone contraption for that? Well you have come to the right place! Now you can recreate it with just command blocks!

---
First, place down an impulse (needs redstone, unconditional) command block containing this command:

```give @p minecraft:fishing_rod[item_name="Stab Shot",custom_data={isStabShot:1b}]```

Place a button on this command block and press it to give yourself the special fishing rod you will need to blow stuff up.

---
Next, place down a repeating (always active, unconditional) command block with this command:

```execute as @a if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run tag @e[type=minecraft:experience_orb] add b4```

This command checks if you are holding the special fishing rod and gives all experience orbs the tag "b4" so that they won't be affected by any of the other command blocks.

---
Next to that repeating command block, place a chain (always active, unconditional) command block and then another next to that one and so on until you have one for every command in this list. Then place these commands one at a time in each command block. For each command in the list, I will say what it does below it.

```execute as @a if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] at @e[type=minecraft:fishing_bobber] at @p run summon minecraft:experience_orb```
> This command checks if you are holding the special fishing rod and if you use it. If so, it will spawn an experience orb.

```execute as @a if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] at @e[type=minecraft:experience_orb,tag=!b4] run summon minecraft:oak_boat ~ ~1000 ~ {Rotation:[0f,90f]}```
> This command checks if you are holding the special fishing rod and spawns an oak boat with a specific rotation at the experience orb.

```execute as @a if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] at @e[type=minecraft:experience_orb,tag=!b4] run summon minecraft:oak_boat ~ ~1000 ~ {Rotation:[0f,-90f]}```
> This command checks if you are holding the special fishing rod and spawns an oak boat with a different rotation than as the oak boat spawned by the previous command. However, just like the previous command, it spawns the oak boat at the experience orb.

```execute as @a if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] as @e[type=minecraft:experience_orb,tag=!b4] at @s rotated as @e[type=minecraft:oak_boat,y=1000,limit=2] positioned ^ ^ ^4 rotated as @e[type=minecraft:oak_boat,y=1000,limit=2] positioned ^ ^ ^-2 rotated as @e[type=minecraft:oak_boat,y=1000,limit=2] positioned ^ ^ ^-4 rotated as @e[type=minecraft:oak_boat,y=1000,limit=2] positioned ^ ^ ^-8 rotated as @e[type=minecraft:oak_boat,y=1000,limit=2] positioned ^ ^ ^-16 rotated as @e[type=minecraft:oak_boat,y=1000,limit=2] positioned ^ ^ ^-32 rotated as @e[type=minecraft:oak_boat,y=1000,limit=2] positioned ^ ^ ^-64 rotated as @e[type=minecraft:oak_boat,y=1000,limit=2] positioned ^ ^ ^-128 run summon minecraft:end_crystal ~ ~ ~ {ShowBottom:0f,Passengers:[{id:"minecraft:end_crystal",ShowBottom:0f}]}```
> This command checks if you are holding the special fishing rod and summons a bunch of end crystals above and below you with even more as their passengers.

```execute as @a if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] at @e[type=minecraft:experience_orb,tag=!b4] positioned ~ ~1000 ~ run kill @e[type=minecraft:oak_boat,distance=..5]```
> This command checks if you are holding the special fishing rod and kills all of the oak_boats that were spawned earlier.

```execute as @a if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] at @e[type=end_crystal] run summon tnt ~ ~ ~ {fuse:0}```
> This command checks if you are holding the special fishing rod and spawns a bunch of tnt to blow up the end crystals. Each peice of tnt has a fuse of zero and no gravity.

```execute as @a if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run kill @e[type=minecraft:fishing_bobber]```
> This command checks if you are holding the special fishing rod and kills the fishing bobber so that the fishing basically automatically retracts.
