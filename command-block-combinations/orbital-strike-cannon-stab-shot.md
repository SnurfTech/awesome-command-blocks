# How to make an Orbital Strike Cannon Stab Shot with just command blocks

Ever wanted that cool Orbital Strike Cannon Stab Shot fishing rod that pratically stabbed into the ground with tnt, destroying almost anything in its path? But you're too lazy to build a huge redstone contraption for that? Well you have come to the right place! Now you can recreate it with just 38 command blocks! (This has raycasting and everything. Make sure you have a beefy computer.)

---
First, place down an impulse (needs redstone, unconditional) command block containing this command:

```
give @p minecraft:fishing_rod[item_name="Stab Shot",custom_data={isStabShot:1b}]
```

Place a button on this command block and press it to give yourself the special fishing rod you will need to blow stuff up.

---
Next, place down a repeating (always active, unconditional) command block with this command:

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] at @s anchored eyes unless entity @e[type=minecraft:armor_stand,tag=stabShotRay] run summon armor_stand ~ ~1.5 ~ {Invisible:1b,Marker:1b,Tags:["stabShotRay"]}
```

This command checks if you are holding and have used the special fishing rod and spawns an invisible armor stand for the raycasting sequence.

---
Next to that repeating command block, place a chain (always active, unconditional) command block and then another next to that one and so on until you have one for every command in this list. Then place these commands one at a time in each command block. For each command in the list, I will say what it does below it.

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run data modify entity @e[tag=stabShotRay,tag=!stabShotRayAligned,limit=1] Rotation set from entity @s Rotation
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run tag @e[type=minecraft:armor_stand,tag=stabShotRay,tag=!stabShotRayAligned] add stabShotRayAligned
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[tag=stabShotRay] at @s if block ~ ~ ~ minecraft:air run tp @s ^ ^ ^10
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-10 air run tag @s add stabShotHit
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-10 air run tp @s ^ ^ ^-10
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-9 air run tag @s add stabShotHit
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-9 air run tp @s ^ ^ ^-9
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-8 air run tag @s add stabShotHit
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-8 air run tp @s ^ ^ ^-8
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-7 air run tag @s add stabShotHit
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-7 air run tp @s ^ ^ ^-7
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-6 air run tag @s add stabShotHit
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-6 air run tp @s ^ ^ ^-6
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-5 air run tag @s add stabShotHit
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-5 air run tp @s ^ ^ ^-5
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-4 air run tag @s add stabShotHit
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-4 air run tp @s ^ ^ ^-4
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-3 air run tag @s add stabShotHit
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-3 air run tp @s ^ ^ ^-3
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-2 air run tag @s add stabShotHit
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-2 air run tp @s ^ ^ ^-2
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-1 air run tag @s add stabShotHit
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ^ ^ ^-1 air run tp @s ^ ^ ^-1
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run execute as @e[type=minecraft:armor_stand,tag=stabShotRay] at @s unless block ~ ~ ~ air run tag @s add stabShotHit
```

```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] run tag @e[type=minecraft:experience_orb] add b4
```

```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] at @s run summon minecraft:experience_orb
```

```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] at @e[type=minecraft:experience_orb,tag=!b4] run summon minecraft:armor_stand ~ ~1000 ~ {Rotation:[0f,90f],Marker:1b,Tags:["stabShotMarker"],Invisible:1b}
```

```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] at @e[type=minecraft:experience_orb,tag=!b4] run summon minecraft:armor_stand ~ ~1000 ~ {Rotation:[0f,-90f],Marker:1b,Tags:["stabShotMarker"],Invisible:1b}
```

```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] as @e[type=minecraft:experience_orb,tag=!b4] at @s rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^4 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-2 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-4 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-8 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-16 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-32 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-64 rotated as @e[type=minecraft:armor_stand,tag=stabShotMarker,y=1000,limit=2] positioned ^ ^ ^-128 run summon minecraft:end_crystal ~ ~ ~ {ShowBottom:0f,Tags:["stabShotCrystal"],Passengers:[{id:"minecraft:end_crystal",ShowBottom:0f,Tags:["stabShotCrystal"]}]}
```

```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] at @e[type=minecraft:experience_orb,tag=!b4] positioned ~ ~1000 ~ run kill @e[type=minecraft:armor_stand,tag=stabShotMarker,distance=..5]
```

```
execute as @e[type=minecraft:armor_stand,tag=stabShotHit] at @e[type=end_crystal,tag=stabShotCrystal] run summon tnt ~ ~ ~ {fuse:0,NoGravity:1b}
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] if entity @e[type=minecraft:armor_stand,tag=stabShotHit] run kill @e[type=minecraft:armor_stand,tag=stabShotHit]
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] unless entity @e[type=minecraft:armor_stand,tag=stabShotRay] run scoreboard players set @s useStabShot 0
```

```
execute as @a unless entity @s[scores={useStabShot=1..}] run kill @e[type=minecraft:armor_stand,tag=stabShotRay]
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] if entity @e[type=minecraft:armor_stand,tag=stabShotRay,distance=200..] run scoreboard players set @s useStabShot 0
```

```
execute as @a[scores={useStabShot=1..}] at @s if items entity @s weapon.* minecraft:fishing_rod[custom_data={isStabShot:1b}] run kill @e[type=minecraft:armor_stand,tag=stabShotRay,distance=200..]
```
