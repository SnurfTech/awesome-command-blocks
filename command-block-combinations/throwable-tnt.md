# How to make throwable tnt with just command blocks

Ever wanted to just throw tnt around, blowing everything up? But you wanna do it in completely vanilla Minecraft? Well you've come to the right place! With just 8 command blocks you can create throwable tnt that you can throw at mobs and blocks.

---
Firstly, place an impulse (needs redstone, unconditional) command block with this command:

```
give @p minecraft:snowball[minecraft:item_name="Throwable TNT",minecraft:item_model=tnt,minecraft:custom_data={isThrowableTNT:1b}]
```

Place a button on it and press it to receive your throwable tnt! However, you cannot use it yet as we need to place more command blocks.

---
Next, anywhere, place a repeating (always active, unconditional) command block with this command:

```
execute as @e[type=snowball,nbt={Item:{components:{"minecraft:custom_data":{isThrowableTNT:1b}}}}] run tag @s add isThrowableTNT
```

This command checks if you have thrown the tnt (which is actually just a retextured snowball), and if so, it applies a tag to it so other command blocks can identify it later.

---
Next to that repeating command block, place a chain (always active, unconditional) command block with this command:

```
execute as @e[type=snowball,tag=isThrowableTNT] at @s unless entity @e[type=marker,tag=isThrowableTNT_marker,distance=..0.5] run summon marker ~ ~ ~ {Tags:["isThrowableTNT_marker","isThrowableTNT_new"]}
```

This command checks if it has already spawned a marker for the snowball and if not, it spawns one with a few tags so other command blocks can identify it later.

---
Next to that chain command block, place another chain (always active, unconditional) command block with this command:

```
execute as @e[type=marker,tag=isThrowableTNT_marker] at @s run tp @s @e[type=snowball,tag=isThrowableTNT,limit=1,sort=nearest,distance=..3]
```

This command constantly teleports the snowball's corresponding marker to the actual snowball.

---
Next to that chain command block, place another chain (always active, unconditional) command block with this command:

```
execute as @e[type=marker,tag=isThrowableTNT_marker,tag=!isThrowableTNT_new] at @s unless entity @e[type=snowball,tag=isThrowableTNT,distance=..2] run kill @e[type=snowball,tag=isThrowableTNT,distance=..5,limit=1,sort=nearest]
```

This command checks if the snowball has disappeared (as in it has hit its target) by checking if its marker is all alone. And if so, it kills the snowball just in case so some throwable tnt exploits are harder to use.

---
Next to that chain command block, place another chain (always active, unconditional) command block with this command:

```
execute as @e[type=marker,tag=isThrowableTNT_marker,tag=!isThrowableTNT_new] at @s unless entity @e[type=snowball,tag=isThrowableTNT,distance=..2] run summon tnt ~ ~ ~ {fuse:0}
```

This command once again checks if the snowball has disappeared by checking if its marker is all alone. And if so, it summons a peice of tnt with a fuse of zero so that it immediately explodes.

---
Next to that chain command block, place another chain (always active, unconditional) command block with this command:

```
execute as @e[type=marker,tag=isThrowableTNT_marker,tag=!isThrowableTNT_new] at @s unless entity @e[type=snowball,tag=isThrowableTNT,distance=..2] run kill @s
```

This command once again checks if the snowball has disappeared by checking if its marker is all alone. And if so, it kills its marker.

---
Next to that chain command block, place another chain (always active, unconditional) command block with this command:

```
tag @e[tag=isThrowableTNT_new] remove isThrowableTNT_new
```

This command removes a tag from whatever marker has it.

---
Now get your throwable tnt and start blowing stuff up!
