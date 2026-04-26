# How to make a car with just command blocks

> Credits to Gecko72 for making the car block model. https://block-display.com/bd/2589/

Ever wanted to drive around in a car in Minecraft that wasn't just one of those incredibly slow redstone machines? Well now you can with just 17 command blocks!

---
Firstly, place a repeating (always active, unconditional) command block with this command:

```
execute at @e[tag=car_engine] as @n[type=player] if data entity @s {RootVehicle:{}} run attribute @n[tag=car_engine] minecraft:movement_speed base reset
```

This command will check if the player is riding an invisible horse with the "car_engine" tag. If so, the horse's movement speed will be reset.

---
Next, place a chain (always active, unconditional) command block next to the repeating command block with this command:

```
execute at @e[tag=car_engine] as @n[type=player] unless data entity @s {RootVehicle:{}} run attribute @n[tag=car_engine] minecraft:movement_speed base set 0
```

This command will check if the player is not riding the invisible horse from earlier. If so, the horse's movement speed will be set to zero.

---
Next, place another chain (always active, unconditional) command block next to the one from earlier with this command:

```
execute as @e[tag=car_skin] at @e[tag=car_engine,limit=1] run tp @s ~ ~ ~ ~ 0
```

This command constantly teleports the actual car block model to the location of the invisible horse so it looks like the horse is actually a car. It also makes sure that the actual car block model cannot "look up" or "look down".

---
Next, place another chain (always active, unconditional) command block next to the one from earlier with this command:

```
execute as @e[tag=car_engine] at @s unless data entity @n[type=player] RootVehicle.Entity{Tags:[car_engine]} unless entity @e[tag=car_marker] run summon marker ~ ~ ~ {Tags:["car_marker"]}
```

This command checks if the player is not riding the invisible horse and checks that the marker that it will spawn doesn't already exist. If so, it will spawn that marker at the current location of the invisible horse.

---
Next, place another chain (always active, unconditional) command block next to the one from earlier with this command:

```
execute as @e[tag=car_engine] at @e[tag=car_marker] rotated as @s run tp @s ~ ~ ~ ~ ~
```

This command constantly teleports the horse to the marker we created earlier as long as it is not being ridden.

---
Next, place another chain (always active, unconditional) command block next to the one from earlier with this command:

```
execute as @e[tag=car_engine] at @s if data entity @n[type=player] RootVehicle.Entity{Tags:[car_engine]} if entity @e[tag=car_marker] run kill @e[tag=car_marker]
```

This command deletes the marker from earlier if the horse is being ridden again.

---
Now, place an impulse (needs redstone, unconditional) command block somewhere. Put a button on it and put this command inside:

```
kill @e[tag=car_engine]
```

This command will get rid of the invisible horse when you are finished using the car. We will soon place some chain command blocks next to this impulse command block so that when you press the button, you can fully get rid of the car when you are finished using it!

---
Next, like I said we were going to do earlier, place a chain (always active, unconditional) command block next to the impulse command block from earlier. Put this command inside of it:

```
kill @e[tag=car_skin]
```

This command will get rid of the car block model.

---
Next, place another chain (always active, unconditional) command block next to the one from earlier with this command:

```
kill @e[tag=car_marker]
```

This command will get rid of the marker that the car is constantly being teleported to.

---
Now, place an impulse (needs redstone, unconditional) command block somewhere. Put a button on it and put this command inside:

```
summon block_display ~-0.5 ~-0.5 ~-0.5 {Passengers:[{id:"minecraft:block_display",block_state:{Name:"minecraft:black_wool",Properties:{}},transformation:[-0.4219f,0f,0f,0.8945f,0f,0.9492f,0f,0.0625f,0f,0f,-0.9492f,2.4716f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,1.0547f,0f,0.3789f,0f,0f,-1.4766f,2.6826f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.1055f,0f,0f,-1.7422f,0f,1.2656f,0f,0.3789f,0f,0f,-1.8984f,1.206f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.1055f,0f,0f,-1.7422f,0f,1.2656f,0f,0.3789f,0f,0f,-1.582f,-0.668f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_wool",Properties:{}},transformation:[-0.4219f,0f,0f,0.8945f,0f,0.9492f,0f,0.0625f,0f,0f,-0.9492f,-1.2198f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_wool",Properties:{}},transformation:[-0.4219f,0f,0f,-1.6367f,0f,0.9492f,0f,0.0625f,0f,0f,-0.9492f,2.4716f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_wool",Properties:{}},transformation:[-0.4219f,0f,0f,-1.6367f,0f,0.9492f,0f,0.0625f,0f,0f,-0.9492f,-1.2198f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:white_stained_glass",Properties:{}},transformation:[-0.3164f,0f,0f,0.2617f,0f,0.3164f,0f,1.0117f,0f,0f,-0.5273f,2.707f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[-0.4219f,0f,0f,1f,0f,0.5273f,0f,0.2734f,0f,0f,-0.5273f,-1.4307f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[-0.4219f,0f,0f,-1.7422f,0f,0.5273f,0f,0.2734f,0f,0f,-0.5273f,-1.4307f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[-0.4219f,0f,0f,-1.7422f,0f,0.5273f,0f,0.2734f,0f,0f,-0.5273f,2.2607f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,0.2109f,0f,0.5898f,0f,0f,-0.2109f,2.788f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:glass",Properties:{}},transformation:[-2.3203f,0f,0f,0.5781f,0f,0.8150495581f,-0.0273047813f,1.75f,0f,-0.2183864875f,-0.1019053429f,1.2305f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.1055f,0f,0f,0.6836f,0f,1.2656f,0f,0.3789f,0f,0f,-1.8984f,1.206f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,0.1055f,0f,0.5898f,0f,0f,-1.8984f,1.2305f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,0.1055f,0f,2.4883f,0f,0f,-1.6875f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,1.0186558153f,0.3821962741f,0.3789f,0f,0.2729862449f,-1.4261760965f,2.3906f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,0.1827235186f,-0.1055135808f,2.4156f,0f,-0.1055135808f,-0.1827235186f,-0.4946f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.1055f,0f,0f,0.6836f,0f,0.9168591456f,-0.0273044339f,1.6445f,0f,-0.2456622623f,-0.101905436f,1.206f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.1055f,0f,0f,0.6836f,0f,0.8438f,0f,1.6445f,0f,0f,-0.1055f,-0.2461f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,0.6814f,0f,0.8438f,0f,1.6445f,1.1602f,0f,0f,-0.2461f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,0.6814f,0f,0.6328f,0f,1.6445f,0.1055f,0f,0f,0.9141f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,0.6814f,0f,0.2109f,0f,1.6445f,0.1055f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.1055f,0f,0f,-1.7422f,0f,0.8438f,0f,1.6445f,0f,0f,-0.1055f,-0.2461f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.1055f,0f,0f,-1.7422f,0f,0.9168591456f,-0.0273044339f,1.6445f,0f,-0.2456622623f,-0.101905436f,1.206f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,-1.7388f,0f,0.8438f,0f,1.6445f,1.1602f,0f,0f,-0.2461f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,-1.7388f,0f,0.2109f,0f,1.6445f,0.1055f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,-1.7388f,0f,0.6328f,0f,1.6445f,0.1055f,0f,0f,0.9141f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,0.4567343978f,-0.3164153785f,1.4174f,0f,-0.263712817f,-0.5480119965f,-1.3797f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,0.6814f,0f,0.5273f,0f,1.6445f,0.9492f,0f,0f,-1.3008f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,0.6814f,0f,0.2109f,0f,2.1719f,0.5273f,0f,0f,-0.8789f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,-1.7388f,0f,0.5273f,0f,1.6445f,0.9492f,0f,0f,-1.3008f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,-1.7388f,0f,0.2109f,0f,2.1719f,0.5273f,0f,0f,-0.8789f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,0.6814f,0f,0.1055f,0f,2.3828f,0.2109f,0f,0f,-0.5625f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,-1.7388f,0f,0.1055f,0f,2.3828f,0.2109f,0f,0f,-0.5625f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:white_stained_glass",Properties:{}},transformation:[-0.3164f,0f,0f,-1.1094f,0f,0.3164f,0f,1.0117f,0f,0f,-0.5273f,2.707f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:orange_stained_glass",Properties:{}},transformation:[-0.2109f,0f,0f,-0.793f,0f,0.2109f,0f,1.0581f,0f,0f,-0.5273f,2.707f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:orange_stained_glass",Properties:{}},transformation:[-0.2109f,0f,0f,-0.1602f,0f,0.2109f,0f,1.0581f,0f,0f,-0.5273f,2.707f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:coal_block",Properties:{}},transformation:[-1.0547f,0f,0f,-0.0547f,0f,0.3164f,0f,1.0117f,0f,0f,-0.5273f,2.7028f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:orange_stained_glass",Properties:{}},transformation:[-0.2109f,0f,0f,-1.6494f,0f,0.1055f,0f,1.1172f,0f,0f,-0.5273f,2.3906f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:orange_stained_glass",Properties:{}},transformation:[-0.2109f,0f,0f,0.6979f,0f,0.1055f,0f,1.1172f,0f,0f,-0.5273f,2.3906f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[-0.1055f,0f,0f,-1.7506f,0f,0.1055f,0f,1.2227f,0f,0f,-0.4219f,0.8086f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[-0.4219f,0f,0f,1f,0f,0.5273f,0f,0.2734f,0f,0f,-0.5273f,2.2607f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:coal_block",Properties:{}},transformation:[-1.1602f,0f,0f,0.0508f,0f,0.4219f,0f,0.4844f,0f,0f,-0.1055f,2.8007f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[0.9492f,0f,0f,-1.0039f,0f,-0.2109f,0f,0.8008f,0f,0f,-0.1055f,2.8091f,0f,0f,0f,1f]},{id:"minecraft:text_display",text:[{"text":"FTU172","color":"#000000","bold":false,"italic":false,"underlined":false,"strikethrough":false,"obfuscated":false,"font":"minecraft:uniform"}],text_opacity:255,background:0,alignment:"center",line_width:220.5,default_background:false,transformation:[1.2656f,0f,0f,-0.523f,0f,1.2656f,0f,0.5266f,0f,0f,1.6875f,2.8462f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:coal_block",Properties:{}},transformation:[1.1602f,0f,0f,-1.1094f,0f,0.4219f,0f,0.8008f,0f,0f,0.1055f,-2.3437f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[-0.9492f,0f,0f,-0.0547f,0f,-0.2109f,0f,1.1172f,0f,0f,0.1055f,-2.3555f,0f,0f,0f,1f]},{id:"minecraft:text_display",text:[{"text":"FTU172","color":"#000000","bold":false,"italic":false,"underlined":false,"strikethrough":false,"obfuscated":false,"font":"minecraft:uniform"}],text_opacity:255,background:0,alignment:"center",line_width:220.5,default_background:false,transformation:[-1.2656f,0f,0f,-0.5356f,0f,1.2656f,0f,0.843f,0f,0f,-1.6875f,-2.3892f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:red_stained_glass",Properties:{}},transformation:[-0.4219f,0f,0f,-1.3203f,0f,0.3164f,0f,1.0117f,0f,0f,-0.5273f,-1.8281f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:red_stained_glass",Properties:{}},transformation:[-0.4219f,0f,0f,0.5781f,0f,0.3164f,0f,1.0117f,0f,0f,-0.5273f,-1.8281f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:orange_stained_glass",Properties:{}},transformation:[-0.4219f,0f,0f,0.5781f,0f,0.2109f,0f,0.8008f,0f,0f,-0.5273f,-1.8281f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:orange_stained_glass",Properties:{}},transformation:[-0.4219f,0f,0f,-1.3203f,0f,0.2109f,0f,0.8008f,0f,0f,-0.5273f,-1.8281f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,0.2109f,0f,0.4844f,0f,0f,-0.2109f,-2.1445f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,0.1827265694f,-0.3164248847f,1.7828f,0f,-0.1055082975f,-0.5480065076f,-1.5907f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.2109f,0f,0f,0.6836f,0f,0.1827296806f,-0.5273645413f,2.3101f,0f,-0.1055029091f,-0.9133885978f,-0.6773f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.2109f,0f,0f,-1.6367f,0f,0.1827296806f,-0.5273645413f,2.3101f,0f,-0.1055029091f,-0.9133885978f,-0.6773f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,0.6814f,0f,0.3164f,0f,1.6445f,0.3164f,0f,0f,-1.6172f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[0f,0f,-0.1055f,-1.7388f,0f,0.3164f,0f,1.6445f,0.3164f,0f,0f,-1.6172f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:black_stained_glass",Properties:{}},transformation:[-2.1094f,0f,0f,0.4727f,0f,0.5272852768f,0.0912828116f,1.8741f,0f,0.9134343583f,-0.052693532f,-1.6434f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_glazed_terracotta",Properties:{facing:"east"}},transformation:[-0.1055f,0f,0f,0.3166f,0f,0.1055f,0f,0.2313f,0f,0f,-0.7383f,-1.9336f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_glazed_terracotta",Properties:{facing:"east"}},transformation:[-0.2109f,0f,0f,0.3672f,0f,0.2109f,0f,0.168f,0f,0f,-0.7383f,-1.5117f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.1055f,0f,0f,0.6836f,0f,1.2656f,0f,0.3789f,0f,0f,-1.582f,-0.668f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,0.9492f,0f,0.4844f,0f,0f,-0.6328f,-1.3797f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-2.5313f,0f,0f,0.6836f,0f,0.1055f,0f,0.5898f,0f,0f,-1.8984f,-0.3516f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,2.3203f,-1.7422f,0f,1.2656f,0f,0.3789f,-0.1055f,0f,0f,-2.1445f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.7383f,0f,0f,0.4727f,0f,0.1055f,0f,0.9063f,0f,0f,-0.9492f,0.7031f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.1562f,0f,0.1055f,0f,1.4336f,0f,0f,-0.1055f,1.2305f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.5781f,0f,0.1055f,0f,0.9063f,0f,0f,-0.9492f,0.7031f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.5781f,0f,1.1602f,0f,0.9063f,0f,0f,-0.1055f,-0.2461f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.2656f,0f,1.1602f,0f,0.9063f,0f,0f,-0.1055f,-0.2461f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.7383f,0f,0f,0.4727f,0f,1.1602f,0f,0.9063f,0f,0f,-0.1055f,-0.2461f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.7383f,0f,0f,0.4727f,0f,0.1055f,0f,1.4336f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.2656f,0f,0.1055f,0f,0.9063f,0f,0f,-0.9492f,0.7031f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.2656f,0f,0.1055f,0f,1.4336f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.2656f,0f,0.1055f,0f,1.5391f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.2656f,0f,0.1055f,0f,1.3281f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.1602f,0f,0.1055f,0f,1.2227f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.0547f,0f,0.1055f,0f,1.1172f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.0508f,0f,0.1055f,0f,1.0117f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.3672f,0f,0.1055f,0f,1.1172f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.2617f,0f,0.1055f,0f,1.0117f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.1562f,0f,0.1055f,0f,1.0117f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.4727f,0f,0.1055f,0f,1.2227f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.5781f,0f,0.1055f,0f,1.3281f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.5781f,0f,0.1055f,0f,1.4336f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.5781f,0f,0.1055f,0f,1.5391f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.4727f,0f,0.1055f,0f,1.6445f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.3672f,0f,0.1055f,0f,1.75f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.2617f,0f,0.1055f,0f,1.8555f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.1562f,0f,0.1055f,0f,1.8555f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,0.0508f,0f,0.1055f,0f,1.8555f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.0547f,0f,0.1055f,0f,1.75f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.1602f,0f,0.1055f,0f,1.6445f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.3164f,0f,0f,0.2617f,0f,0.1055f,0f,1.5391f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.3164f,0f,0f,0.2617f,0f,0.1055f,0f,1.3281f,0f,0f,-0.1055f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:netherite_block",Properties:{}},transformation:[0f,0f,-0.0169f,0.0771f,0f,-0.0169f,0f,0.8535f,-0.1055f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:netherite_block",Properties:{}},transformation:[0.000064414f,0.000014872f,-0.016898271f,0.0771f,0.0913894322f,-0.0084382423f,2.1e-8f,0.8535f,-0.0526873133f,-0.0146396266f,-0.0000154583f,0.9404f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[0.0000255132f,-0.000015207f,-0.1054997429f,0.0972f,-0.0547794174f,-0.0163198869f,0.0000884137f,0.959f,-0.2036611024f,0.0043896227f,-0.0000365623f,0.9404f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[0.0000255132f,-0.000015207f,-0.1054997429f,0.2881f,-0.0547794174f,-0.0163198869f,0.0000884137f,0.959f,-0.2036611024f,0.0043896227f,-0.0000365623f,0.9404f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:netherite_block",Properties:{}},transformation:[0.000064414f,0.000014872f,-0.016898271f,0.2881f,0.0913894322f,-0.0084382423f,2.1e-8f,0.8535f,-0.0526873133f,-0.0146396266f,-0.0000154583f,0.9404f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:netherite_block",Properties:{}},transformation:[0f,0f,-0.0169f,0.2881f,0f,-0.0169f,0f,0.8535f,-0.1055f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.7383f,0f,0f,-0.8984f,0f,0.1055f,0f,0.9063f,0f,0f,-0.9492f,0.7031f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-1.6367f,0f,0.1055f,0f,0.9063f,0f,0f,-1.0547f,0.7031f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.793f,0f,0.1055f,0f,0.9063f,0f,0f,-0.9492f,0.7031f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-0.793f,0f,1.1602f,0f,0.9063f,0f,0f,-0.1055f,-0.2461f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:gray_wool",Properties:{}},transformation:[-0.1055f,0f,0f,-1.6367f,0f,1.1602f,0f,0.9063f,0f,0f,-0.1055f,-0.2461f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[-0.7383f,0f,0f,-0.8984f,0f,1.1602f,0f,0.9063f,0f,0f,-0.1055f,-0.2461f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:iron_block",Properties:{}},transformation:[-0.1055f,0f,0f,0.6962f,0f,0.1055f,0f,1.2227f,0f,0f,-0.4219f,0.8086f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:glass",Properties:{}},transformation:[0f,0f,-0.3164f,1.2109f,0f,0.2109f,0f,1.6445f,0.1055f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,-0.1055f,1.3164f,0f,0.2109f,0f,1.6445f,0.2109f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,-0.1055f,0.8945f,0f,0.2109f,0f,1.6445f,0.2109f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,-0.5273f,1.3164f,0f,0.1055f,0f,1.5391f,0.2109f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,-0.5273f,1.3164f,0f,0.1055f,0f,1.8555f,0.2109f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,-0.3164f,1.2109f,0f,0.2109f,0f,1.6445f,0.1055f,0f,0f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:blackstone",Properties:{}},transformation:[0.0000200601f,0.2037000058f,-0.0273126719f,0.6435f,-0.000008089f,0.0546089795f,0.1018982964f,1.6841f,0.1054952354f,-0.0000253502f,0.0000165367f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:glass",Properties:{}},transformation:[0f,0f,-0.3164f,-2.0586f,0f,0.2109f,0f,1.6445f,0.1055f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,-0.1055f,-1.9531f,0f,0.2109f,0f,1.6445f,0.2109f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,-0.1055f,-2.375f,0f,0.2109f,0f,1.6445f,0.2109f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,-0.5273f,-1.9531f,0f,0.1055f,0f,1.5391f,0.2109f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,-0.5273f,-1.9531f,0f,0.1055f,0f,1.8555f,0.2109f,0f,0f,1.0195f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:light_blue_terracotta",Properties:{}},transformation:[0f,0f,-0.3164f,-2.0586f,0f,0.2109f,0f,1.6445f,0.1055f,0f,0f,1.125f,0f,0f,0f,1f]},{id:"minecraft:block_display",block_state:{Name:"minecraft:blackstone",Properties:{}},transformation:[-0.00000925f,0.1827372508f,0.0526975428f,-1.9795f,-2e-10f,-0.1054977239f,0.0912820203f,1.7896f,0.105501321f,0.000013733f,0.0000026405f,1.0195f,0f,0f,0f,1f]}]}
```

This command creates the car block model. There will be other chain command blocks next to it that will do other things. In the end, you will be able to press the button on this command block to spawn the car.

---
Next, place a chain (always active, unconditional) command block next to the impulse command block from earlier. Put this command inside:

```
tag @e[type=block_display,distance=..5] add car_skin
```

This command applies the tag "car_skin" to the car block display so other command blocks can identify it later.

---
Next, place another chain (always active, unconditional) command block next to the one from earlier and put this command inside:

```
tag @e[type=text_display,distance=..5] add car_skin
```

This command applies the tag "car_skin" to the car block display's text displays so other command blocks can identify the text displays with the block displays later.

---
Next, place another chain (always active, unconditional) command block next to the one from earlier and put this command inside:

```
summon horse ~ ~ ~-4 {Tame:1b,Tags:["car_engine"],Silent:1b,DeathLootTable:"minecraft:empty"}
```

This command will summon the invisble horse and make sure it doesn't make any noise, doesn't drop anything on death, is automatically tamed, and has the "car_engine" tag.

---
Next, place another chain (always active, unconditional) command block next to the one from earlier and put this command inside:

```
effect give @e[tag=car_engine] minecraft:invisibility infinite 1 true
```

This command will give the horse its actual invisibility effect. It will make sure it emits no particles and stays on it forever.

---
Next, place another chain (always active, unconditional) command block next to the one from earlier and put this command inside:

```
item replace entity @e[tag=car_engine] saddle with minecraft:saddle 1
```

This command will give the invisible horse a saddle so it can be controlled while being ridden.

---
Next, place another chain (always active, unconditional) command block next to the one from earlier and put this command inside:

```
attribute @n[tag=car_engine] minecraft:scale base set 0.65
```

This command will make the invisible horse smaller than it already is. This is because if it was its default size, when riding it, your head would be sticking out through the roof of the car. It also makes the saddle on it that cannot be turned invisible a little bit less intrusive.

---
Next, place another chain (always active, unconditional) command block next to the one from earlier and put this command inside:

```
attribute @n[tag=car_engine] minecraft:jump_strength base set 0
```

This command will make the invisible horse unable to jump. This is because it would look very wierd if you saw your car jumping around.

---
Now you can press the button that spawns the car and (it may take a few tries) try to "ride" the invisible horse. If you can't find it, then it will always be at the front seat. So you basically want to try to "ride" the front seat of the car. Then you can press the button that gets rid of the car when you want to stop driving.
