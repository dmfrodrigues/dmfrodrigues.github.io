---
layout: project
title: "The Cursed Catacombs"
permalink: /projects/the-cursed-catacombs
github: https://github.com/dmfrodrigues/feup-lpoo-proj
---

<div class="scroll" markdown="1">
![animation](https://raw.githubusercontent.com/dmfrodrigues/feup-lpoo-proj/master/docs/images/pacman-20200531-192912.gif)
![menus-gif](https://raw.githubusercontent.com/dmfrodrigues/feup-lpoo-proj/master/docs/images/pacman-20200531-193722.gif)
</div>

You are a noble knight seeking to assist Her Majesty in cleansing the capital's catacombs from the many monsters that inhabit it. Your mission is to kill all monsters and collect as many coins as possible across multiple levels.

This project was developed by:
- [Diogo Rodrigues](https://github.com/dmfrodrigues) ([dmfrodrigues2000@gmail.com](mailto:dmfrodrigues2000@gmail.com)/[diogo.rodrigues@fe.up.pt](mailto:diogo.rodrigues@fe.up.pt))
- [João Matos](https://github.com/MechJM) ([up201703884@fe.up.pt](mailto:up201703884@fe.up.pt))

## Releases

We unfortunately failed at creating a working executable fat jar (or any sort of working jar), meaning you'll have to build from source.
Use the following commands to build/run the project:
```sh
./gradlew build     # Just build
./gradlew run       # Build if necessary, and run
```

| Releases | Source code                                                                   |
|----------|-------------------------------------------------------------------------------|
| final    | [final.zip](https://github.com/dmfrodrigues/feup-lpoo-proj/archive/final.zip) |

## Description

Her Majesty the Queen has requested the assistance of a noble knight to cleanse the catacombs of the Kingdom's capital of the terrible monsters that have been haunting her subjects for centuries. Unfortunately, because people are scared of the monsters that occasionally escape the catacombs, productivity is low and the Kingdom's coffers are empty (otherwise she would have hired a professional ghost-hunter team), but whoever answers Her Majesty's call will have rights over any treasure found in the catacombs.

Having accepted the challenge, your goal is to kill all monsters, while collecting as many coins as possible so as to guarantee an alternative to the rather under-financed Kingdom's Social Security system for yourself.

The catacombs are full of treasures from ancient times, as well as weapons from those who once ventured into the depths of the city but never returned.

- **Q: Do what?** A: Kill monsters and collect coins.
- **Q: With what?** A: You start with a knife, but you can catch other weapons and bullets in the catacombs.
- **Q: How do I leave the catacombs?** A: You may take a rest or leave at any time, but your mission is only over once you cleanse all the catacombs of the city.
- **Q: What if I die?** A: Her Majesty has been personally appointed by God, if you die on duty He will give you a second chance.

### Controls

- Everywhere:
    - `D` to enable/disable debug information (FPS), on the lower left corner.

- In menus:
    - `⬆`/`⬇` to navigate up/down the menu items.
    - `↵` (Enter) to select an item.
    - `ESC` to go to the previous menu.
    - `ESC`/`P` to unpause the game.

- In game:
    - `⬅`/`⬆`/`➡`/`⬇` to move hero west/north/east/south.
    - `⎵` (Space bar) to use melee attack.
    - `F` to shoot a bullet.
    - `ESC`/`P` to pause the game.

### Elements

| Item      | Image                                                                                                                                         | Description |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Wall      | ![wall](https://github.com/dmfrodrigues/feup-lpoo-proj/raw/master/docs/images/wall.png)       | No-one can go over a wall |
| Coin      | ![coin](https://github.com/dmfrodrigues/feup-lpoo-proj/raw/master/docs/images/coin.png)       | Just a coin |
| Sword     | ![sword](https://github.com/dmfrodrigues/feup-lpoo-proj/raw/master/docs/images/sword.png)     | If you catch it, you can deal more melee damage |
| Potion    | ![potion](https://github.com/dmfrodrigues/feup-lpoo-proj/raw/master/docs/images/potion.png)   | Restore some health |
| Hero      | ![hero](https://github.com/dmfrodrigues/feup-lpoo-proj/raw/master/docs/images/hero.png)       | Yourself |
| Ghost     | ![ghost](https://github.com/dmfrodrigues/feup-lpoo-proj/raw/master/docs/images/ghost.png)     | Follows you, can go over other enemies; is not affected by bullets |
| Ogre      | ![ogre](https://github.com/dmfrodrigues/feup-lpoo-proj/raw/master/docs/images/ogre.png)       | Stronger, follows you |
| Mummy     | ![mummy](https://github.com/dmfrodrigues/feup-lpoo-proj/raw/master/docs/images/mummy.png)     | Like an ogre, but not as strong; follows you |
| Guard     | ![guard](https://github.com/dmfrodrigues/feup-lpoo-proj/raw/master/docs/images/guard.png)     | Follows a pre-determined path, will only attack you if within melee range |
