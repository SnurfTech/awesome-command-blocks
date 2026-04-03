# How to make a jetpack in minecraft with just commands

Ever wanted to fly in survival mode? Now you can if you have this jetpack in your chestplate slot! Just sneak to start flying and look down whilst sneaking to slowly and safely decend back to the ground.

---
Firstly, place an impulse (needs redstone) command block with this command:

```give @p copper_chestplate[item_name="Jetpack",custom_data={is_jetpack:1b},minecraft:unbreakable={},minecraft:attribute_modifiers=[]] 1```

This command will give you the jetpack that you need to fly with. Place a button on the impulse command block and press it to receive your jetpack.

---
Next to that impulse command block, place a chain (always active) command block with this command:

```scoreboard objectives add jetpack minecraft.custom:minecraft.sneak_time```

Optionally you could not do this and run this command in chat once and skip placing this command block, but I like to do this so I don't have to save the command elsewhere for if I want to have a jetpack in another world. It also satifies my OCD. What this command does is it makes it possible to detect whenever you are sneaking.

---
Next, anywhere, place a repeating (always active) command block with this command:

```execute as @a[scores={jetpack=1..},x_rotation=-90..80] if items entity @s armor.chest copper_chestplate[custom_data={is_jetpack:1b}] run effect give @s levitation 1 8 true```

This command checks if you are sneaking, have the jetpack equipped, and are not facing down. If so, it will give you levitation so you start flying.

---
Next to the repeating command block from earlier, place a chain (always active) command block with this command:

```execute as @a[scores={jetpack=1..},x_rotation=81..90] if items entity @s armor.chest copper_chestplate[custom_data={is_jetpack:1b}] run effect give @s slow_falling 1 4 true```

This command checks if you are sneaking and have the jetpack equipped as well. However, it checks if you are facing down. If so, it gives you slow falling so you can decend safely.

---
Next to the chain command block from earlier, place another chain (always active) command block with this command:

```execute as @a[scores={jetpack=1..}] at @s if items entity @s armor.chest copper_chestplate[custom_data={is_jetpack:1b}] run playsound entity.wither.shoot master @s ~ ~ ~ .03 .85```

This command checks if you are sneaking and have the jetpack equipped once again. If so, it plays a jetpack engine-like noise at your current location.

---
Next to the chain command block from earlier, place another chain (always active) command block with this command:

```scoreboard players reset @a[scores={jetpack=1..}] jetpack```

This command resets the scoreboard that records when you sneak.

---
Now equip your jetpack in your chestplate slot, sneak, and start flying! Don't forget that you can safely decend by sneaking and looking down.
