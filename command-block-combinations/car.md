# How to make a car with just command blocks

> credits to Gecko72 for the car block model. https://block-display.com/bd/2589/

Ever wanted to drive around in a car in Minecraft that wasn't just one of those incredibly slow redstone machines? Well now you can with just 17 command blocks!

---
Firstly, place a repeating (always active) command block with this command:

```execute at @e[tag=car_engine] as @n[type=player] if data entity @s {RootVehicle:{}} run attribute @n[tag=car_engine] minecraft:movement_speed base reset```

This command will check if the player is riding an invisible horse with the "car_engine" tag. If so, the horse's movement speed will be reset.

---
Next, place a chain (always active) command block next to the repeating command block with this command:

```execute at @e[tag=car_engine] as @n[type=player] unless data entity @s {RootVehicle:{}} run attribute @n[tag=car_engine] minecraft:movement_speed base set 0```

This command will check if the player is not riding the invisible horse from earlier. If so, the horse's movement speed will be set to zero.

---
Next, place another chain (always active) command block next to the one from earlier with this command:

```execute as @e[tag=car_skin] at @e[tag=car_engine,limit=1] run tp @s ~ ~ ~ ~ 0```

This command constantly teleports the actual car block model to the location of the invisible horse so it looks like the horse is actually a car. It also makes sure that the actual car block model cannot "look up" or "look down".

---
Next, place another chain (always active) command block next to the one from earlier with this command:

```execute as @e[tag=car_engine] at @s unless data entity @n[type=player] RootVehicle.Entity{Tags:[car_engine]} unless entity @e[tag=car_marker] run summon marker ~ ~ ~ {Tags:["car_marker"]}```

This command checks if the player is not riding the invisible horse and checks that the marker that it will spawn doesn't already exist. If so, it will spawn that marker at the current location of the invisible horse.

---
Next, place another chain (always active) command block next to the one from earlier with this command:

```execute as @e[tag=car_engine] at @e[tag=car_marker] rotated as @s run tp @s ~ ~ ~ ~ ~```

This command constantly teleports the horse to the marker we created earlier as long as it is not being ridden.

---
Next, place another chain (always active) command block next to the one from earlier with this command:

```execute as @e[tag=car_engine] at @s if data entity @n[type=player] RootVehicle.Entity{Tags:[car_engine]} if entity @e[tag=car_marker] run kill @e[tag=car_marker]```

This command deletes the marker from earlier if the car is being ridden again.

---
Now, place an impulse (needs redstone) command block somewhere. Put a button on it and put this command inside:

```kill @e[tag=car_engine]```

This command will
