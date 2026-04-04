# How to make a treefeller axe with just command blocks

Don't we all hate how we have to mine a whole tree one block at a time just to get all the resources from it? I sure do! (Especially for the really big trees.) So I made a treefeller axe that makes it so you only need to break one block and the whole tree breaks and drops its loot with just 21 command blocks! (This only works in survival mode where loot drops from breaking blocks.) Also, this is an extremely rudimentary design that could be highly improved. However, the amount of command blocks required for that would be absurd and I'm to lazy. So just don't go mining in a forest because you might mine out the whole thing instantly if the trees are connected and crash your game.

---
Firstly, place an impulse (always active, unconditional) command block with this command:

```give @p minecraft:golden_axe[item_name="Treefeller Axe",custom_data={isMagicAxe:1b}]```

Place a button on this command block and press it to acquire the actual treefeller axe.

---
Next, place a row of always active, unconditional command blocks and for each command in the list below, put it in one of the command blocks. Make sure the first one is a repeating command block and the rest are chain command blocks. (It doesn't really matter which order you put this all in, but for organization purposes, I recommended putting them in the order that I provide them in.) What all of these command blocks will do is each of them manages the breaking of one log type or one leaf type.

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item, nbt={Item:{id:"minecraft:oak_log"}}] run fill ~2 ~2 ~2 ~-2 ~-2 ~-2 air replace minecraft:oak_log destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item] run fill ~3 ~3 ~3 ~-3 ~-3 ~-3 air replace minecraft:oak_leaves destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item, nbt={Item:{id:"minecraft:spruce_log"}}] run fill ~2 ~2 ~2 ~-2 ~-2 ~-2 air replace minecraft:spruce_log destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item] run fill ~3 ~3 ~3 ~-3 ~-3 ~-3 air replace minecraft:spruce_leaves destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item, nbt={Item:{id:"minecraft:dark_oak_log"}}] run fill ~2 ~2 ~2 ~-2 ~-2 ~-2 air replace minecraft:dark_oak_log destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item] run fill ~3 ~3 ~3 ~-3 ~-3 ~-3 air replace minecraft:dark_oak_leaves destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item, nbt={Item:{id:"minecraft:birch_log"}}] run fill ~2 ~2 ~2 ~-2 ~-2 ~-2 air replace minecraft:birch_log destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item] run fill ~3 ~3 ~3 ~-3 ~-3 ~-3 air replace minecraft:birch_leaves destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item, nbt={Item:{id:"minecraft:acacia_log"}}] run fill ~2 ~2 ~2 ~-2 ~-2 ~-2 air replace minecraft:acacia_log destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item] run fill ~3 ~3 ~3 ~-3 ~-3 ~-3 air replace minecraft:acacia_leaves destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item, nbt={Item:{id:"minecraft:mangrove_log"}}] run fill ~2 ~2 ~2 ~-2 ~-2 ~-2 air replace minecraft:mangrove_log destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item] run fill ~3 ~3 ~3 ~-3 ~-3 ~-3 air replace minecraft:mangrove_leaves destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item, nbt={Item:{id:"minecraft:pale_oak_log"}}] run fill ~2 ~2 ~2 ~-2 ~-2 ~-2 air replace minecraft:pale_oak_log destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item] run fill ~3 ~3 ~3 ~-3 ~-3 ~-3 air replace minecraft:pale_oak_leaves destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item, nbt={Item:{id:"minecraft:warped_stem"}}] run fill ~2 ~2 ~2 ~-2 ~-2 ~-2 air replace minecraft:warped_stem destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item] run fill ~1 ~1 ~1 ~-1 ~-1 ~-1 air replace minecraft:warped_wart_block destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item, nbt={Item:{id:"minecraft:crimson_stem"}}] run fill ~2 ~2 ~2 ~-2 ~-2 ~-2 air replace minecraft:crimson_stem destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item] run fill ~1 ~1 ~1 ~-1 ~-1 ~-1 air replace minecraft:nether_wart_block destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item, nbt={Item:{id:"minecraft:jungle_log"}}] run fill ~2 ~2 ~2 ~-2 ~-2 ~-2 air replace minecraft:jungle_log destroy```

```execute as @a if items entity @s weapon.* minecraft:golden_axe[custom_data={isMagicAxe:1b}] at @e[type=item] run fill ~3 ~3 ~3 ~-3 ~-3 ~-3 air replace minecraft:jungle_leaves destroy```
