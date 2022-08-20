# Inventory Parser for Minecraft 1.19

Inventory Parser is a side-datapack which provides far more convineint access to the player's Inventory NBT via `/data` command.

Previously, the number of all cases of parsing each slot in the inventory had to be implemented within mcfunction.

Inventory Parser makes this procedure more convenient by using `storage`.

## Installation

1. Download this repository.
2. Put this datapack on your datapack/data/ folder and execute load.mcfunction and tick.mcfunction in your datapack or, apply this datapack on your server which needs this functionality

## How to Use

This datapack provides a simple functionality.

You can get the player's information of item of specific slot through  `/data` command.

but how to modify player's data? It needs to be implemented all of the cases by default.

you can just modify player Item's nbt and apply by just adding the tag named `invparse:nb` into your item.  
the number `n` should be unique.

## Usage

### 1. Query

query the item which has the tag named `invparse`, which value is same with `.query` value in `invparse` scoreboard.

```mcfunction
# get item from player's inventory through query

scoreboard players set .query invparse 1
function invparse:query
```

also, you can modify the item's information. (this is main point.)

```mcfunction
# e.g. see the information the item that you got.
data get storage invparse:parsed
```
### 2. Update

the second functionality is the `update` calculation.  
you can reflect your modified item into player's inventory, which could modify player's inventory without limit that player nbt cannot be modified.

```mcfunction
# after work, return the modified item into container where the queried item is.

# replacing item into player's container where the queried item is.

scoreboard players set .query invparse 2
function invparse:update
```

## Optimization

you can also try optimizing by just quering only hotbar and left hand.

- `query_hotbar.mcfunction` : query only hotbar and left hand.

```mcfunction
# e.g
scoreboard players set .query invparse 3
function invparse:query_hotbar
```

## Version

added query optimizing options. 0.1.0

## License

This project is under the MIT LICENSE.

if there is a bug, please notice me with pull request. I will welcome it and accept it.