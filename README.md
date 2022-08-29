# Dark Forest - Java Game

## Disclamore!

This game was developed as a semester work at the university and is not a finished product. I had no previous experience in developing in java and especially games.

## Topic

The topic of the semester work is a game engine for Real time RPG games in open world with 2D top view.

All control in the game will be by keyboard. The player will have an inventory to store different items and will also be able to equip some of them to improve their properties (protection or damage).

There will also be monsters in the game that the player will be able to fight in real time.

There is no objective in the game, it's an RPG sandbox.

## Goals

The aim of the project is:

1. To create a simple game engine that will allow to create a simple game with almost no code changes, just by specifying the configuration.
2. Learn how to work with the architecture.
3. Learn OOP.

## Basic user documentation

### Main Menu

Once the user launches the application, the main menu is displayed.

![image](https://user-images.githubusercontent.com/30042943/178839527-e3eb28e6-36f2-47a0-ba43-5e2a5c6ad6e0.png)

### Game World

Next, the user presses the "Start Game" button to begin the game. The player will find himself in an open world. The player can navigate the map using the **W**, **A**, **S**, **D** keys.

![image](https://user-images.githubusercontent.com/30042943/178840949-e41a7db9-089f-410d-95a7-fe5a5c28336a.png)

### Combat system

Using the "**J**" key, the player can attack the enemy. Each monster has its own speed, visibility and attack radius. If a monster notices you, it will move after you until it dies, until you kill it or change location (through a portal).

![image](https://user-images.githubusercontent.com/30042943/178839964-4586c665-929f-4f9a-b706-54bf11d18c83.png)

### Game Menu

During the game the player can open the game menu by pressing a key **Escape**. During this time the game will be paused. In the game menu the player can exit to the main menu, save the game, load the game or exit the game.

![image](https://user-images.githubusercontent.com/30042943/178841445-ccfc4c17-7c9c-46c1-984a-56e0c09b6c9b.png)

### Inventory

The player can collect various items on the map, which he can then see in his inventory, which he can go to by pressing **I**. There will only be three types of items in the game (**weapons**, **armor** and **healing potions**). The player will be able to equip weapons and armor and use potions.

![image](https://user-images.githubusercontent.com/30042943/178840251-7eb2c81a-1539-4bc5-b78e-1d6297944a67.png)

The player can also select items in the inventory using the **W**, **A**, **S**, **D** keys, put on or take off an item using the **J** key, use an item using the **K** key, and delete an item using the **L** key. The currently selected item and items that are already equipped will stand out with different colors. To return back to the game, the player can use the "Escape" key.

### Portals

There are portals in the game that allow you to move between locations.

![image](https://user-images.githubusercontent.com/30042943/178841855-1531919b-43cd-49ee-a9ea-18f4449cd6d5.png)

### End game

If the player dies, the game will start again.

![image](https://user-images.githubusercontent.com/30042943/178840701-35adb011-6bca-4081-8498-1b8e45bdfed4.png)

## Technical description

I tried my best to separate the main parts of the game to make it easier to expand.

The JavaFX library is used for graphics. The game world is rendered using canvas.

Almost everything in the game can be set up with configuration files, without the need to change the game code. 

### Configuration

#### Player

Example player configuration.

```
{
  "name": "Mikita",
  "initialHealth": 500,
  "health": 500,
  "damage": 50,
  "armor": 0,
  "damageRadius": 10,
  "locationId": 1,
  "positionX": 17,
  "positionY": 9,
  "equippedWeaponId": 4,
  "equippedArmorId": -1,
  "inventory": [1, 5]
}
```

#### Map

Example map configuration. Each character represents a separate tile.

```
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABBBBBB
AAAABBBBBBBBBBBBBAAAAAAAAAAAAAAAAAAABBBBBBB
AAAABBBBBBBBBBBBBAAAAAAAAAAAAAABBBBBBBBBBBB
AAAAAAAAAAAAAAAAAAAAABBBBBBBBBBBBAAABBBBBBB
AAAAAAAAAAAAAAAAAAAAABBBBBBBBBBBBAAABBBBBBB
AAAAAAAAAAAAAAAAAAAAAAAAAAAABBBBBBBBBBBBBBB
AAAAAAAAAAAAAABAAAABAAAAAAABBBBBBAAAAAAAAAA
AAAAAAAAABAAAAAAABAAAABAAAAAAAAAAAAAAAAAAAA
AAABAAAAAAAABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAABBBBBAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAABBBBBAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAABBBBBAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
```

#### Tile

```
{
  "id": "A",
  "passable": true
}
```

#### Location

```
{
  "id": 1,
  "name": "Dark forest",
  "portals": [
    {
      "id": 1,
      "positionX": 27,
      "positionY": 7
    }
  ],
  "items": [
    {
      "id": 1,
      "positionX": 36,
      "positionY": 9
    },
    {
      "id": 2,
      "positionX": 35,
      "positionY": 13
    },
    {
      "id": 3,
      "positionX": 11,
      "positionY": 9
    },
    {
      "id": 4,
      "positionX": 10,
      "positionY": 3
    },
    {
      "id": 7,
      "positionX": 13,
      "positionY": 11
    }
  ],
  "monsters": [
    {
      "id": 1,
      "positionX": 36,
      "positionY": 9
    },
    {
      "id": 2,
      "positionX": 35,
      "positionY": 11
    },
    {
      "id": 1,
      "positionX": 10,
      "positionY": 3
    },
    {
      "id": 3,
      "positionX": 7,
      "positionY": 12
    }
  ]
}
```

#### Portal

```
{
  "id": 1,
  "locationId": 2,
  "playerX": 13,
  "playerY": 5
}
```

#### Item

```
{
  "id": 6,
  "name": "Sphere of death",
  "type": "weapon",
  "damage": 100,
  "radius": 50
}
```

#### Enemy

```
{
  "id": 1,
  "name": "Life Eater",
  "health": 350,
  "damage": 20,
  "damageRadius": 20,
  "viewingRadius": 64,
  "speed": 70,
  "attackSpeed": 1000
}
```
