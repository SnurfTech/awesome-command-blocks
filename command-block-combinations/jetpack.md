# How to make a jetpack in minecraft with just commands

Ever wanted to fly in survival mode? Now you can if you have this jetpack in your chestplate slot! Just sneak to start flying and look down whilst sneaking to slowly and safely decend back to the ground.

> Put this single command in an activated command block to place all the command blocks at once:
> ```
> summon falling_block ~ ~1 ~ {BlockState:{Name:redstone_block},Passengers:[{id:falling_block,BlockState:{Name:activator_rail}},{id:command_block_minecart,Command:'tellraw @p [{"text":"Thanks for using Command Block Assembler! \\nAlso thanks to Mr. Papaveraceae for their support on ","color":"green"},{"text":"Patreon","color":"gold","clickEvent":{"action":"open_url","value":"https://patreon.com/GalSergey"},"hoverEvent":{"action":"show_text","value":"Go to Patreon"}},"."]'},{id:command_block_minecart,Command:"scoreboard objectives add jetpack minecraft.custom:minecraft.sneak_time"},{id:command_block_minecart,Command:"setblock ~1 ~ ~ minecraft:command_block[facing=east]{Command:'give @p copper_chestplate[item_name=\"Jetpack\",custom_data={is_jetpack:1b},minecraft:unbreakable={},minecraft:attribute_modifiers=[]] 1'}"},{id:command_block_minecart,Command:"setblock ~2 ~ ~ minecraft:repeating_command_block[facing=east]{auto:1b,Command:'execute as @a[scores={jetpack=1..},x_rotation=-90..80] if items entity @s armor.chest copper_chestplate[custom_data={is_jetpack:1b}] run effect give @s levitation 1 8 true'}"},{id:command_block_minecart,Command:"setblock ~3 ~ ~ minecraft:chain_command_block[facing=east]{auto:1b,Command:'execute as @a[scores={jetpack=1..},x_rotation=81..90] if items entity @s armor.chest copper_chestplate[custom_data={is_jetpack:1b}] run effect give @s slow_falling 1 4 true'}"},{id:command_block_minecart,Command:"setblock ~4 ~ ~ minecraft:chain_command_block[facing=east]{auto:1b,Command:'execute as @a[scores={jetpack=1..}] at @s if items entity @s armor.chest copper_chestplate[custom_data={is_jetpack:1b}] run playsound entity.wither.shoot master @s ~ ~ ~ .03 .85'}"},{id:command_block_minecart,Command:"setblock ~5 ~ ~ minecraft:chain_command_block[facing=east]{auto:1b,Command:'scoreboard players reset @a[scores={jetpack=1..}] jetpack'}"},{id:command_block_minecart,Command:"setblock ~1 ~ ~-1 minecraft:oak_button[facing=north]"},{id:command_block_minecart,Command:"setblock ~1 ~ ~1 minecraft:oak_button[facing=south]"},{id:command_block_minecart,Command:"setblock ~2 ~ ~-1 oak_wall_sign[facing=north]{front_text:{has_glowing_text:1b,messages:['','Give Jetpack','--->','']}}"},{id:command_block_minecart,Command:"setblock ~2 ~ ~1 oak_wall_sign[facing=south]{front_text:{has_glowing_text:1b,messages:['','Give Jetpack','<---','']}}"},{id:command_block_minecart,Command:"setblock ~ ~1 ~ command_block{Command:\"fill ~ ~ ~ ~ ~-3 ~ air\",auto:1}"},{id:command_block_minecart,Command:"execute align xyz run kill @e[type=command_block_minecart,dy=0]"}]}
> ```
> This single command was made with [Command Block Assembler](https://far.ddns.me/command_block_assembler)

---
Firstly, type this command in the chat:

```
/scoreboard objectives add jetpack minecraft.custom:minecraft.sneak_time
```

Running this command makes it possible to detect whenever you are sneaking.

---
Next, place an impulse (needs redstone, unconditional) command block with this command:

```
give @p copper_chestplate[item_name="Jetpack",custom_data={is_jetpack:1b},minecraft:unbreakable={},minecraft:attribute_modifiers=[]] 1
```

This command will give you the jetpack that you need to fly with. Place a button on the impulse command block and press it to receive your jetpack.

---
Next, anywhere, place a repeating (always active, unconditional) command block with this command:

```
execute as @a[scores={jetpack=1..},x_rotation=-90..80] if items entity @s armor.chest copper_chestplate[custom_data={is_jetpack:1b}] run effect give @s levitation 1 8 true
```

This command checks if you are sneaking, have the jetpack equipped, and are not facing down. If so, it will give you levitation so you start flying.

---
Next to the repeating command block from earlier, place a chain (always active, unconditional) command block with this command:

```
execute as @a[scores={jetpack=1..},x_rotation=81..90] if items entity @s armor.chest copper_chestplate[custom_data={is_jetpack:1b}] run effect give @s slow_falling 1 4 true
```

This command checks if you are sneaking and have the jetpack equipped as well. However, it checks if you are facing down. If so, it gives you slow falling so you can decend safely.

---
Next to the chain command block from earlier, place another chain (always active, unconditional) command block with this command:

```
execute as @a[scores={jetpack=1..}] at @s if items entity @s armor.chest copper_chestplate[custom_data={is_jetpack:1b}] run playsound entity.wither.shoot master @s ~ ~ ~ .03 .85
```

This command checks if you are sneaking and have the jetpack equipped once again. If so, it plays a jetpack engine-like noise at your current location.

---
Next to the chain command block from earlier, place another chain (always active, unconditional) command block with this command:

```
scoreboard players reset @a[scores={jetpack=1..}] jetpack
```

This command resets the scoreboard that records when you sneak.

---
Now equip your jetpack in your chestplate slot, press sneak, and start flying! Don't forget that you can safely decend by sneaking and looking down.
