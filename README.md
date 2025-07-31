<p align="center">
  <img src="https://venturebeat.com/wp-content/uploads/2022/11/press_release_banner.jpg" width="800">
</p>

<h1 align="center">[Discord] - FarmMergeValley Injector</h1>

FMV Injector lets you set up various methods for modifying content in the Farm Merge Valley Discord game. This project is based on @wooslow's repository on the same subject. For best results, perform these steps using Google Chrome. There is no guarantee that these methods will work on other browsers.
<br><br>
These methods violate the game developers' rules, and many bans have already occurred. I take no responsibility for your actions. Use this tool only if you fully understand the risks involved.

---

## Features

* [x] \- [giveInventoryItem](https://github.com/AstraaDev/Discord-FarmMergeValley-Injector) - Obtain unlimited quantities of any item.
* [x] \- [spawnUpgradeCard](https://github.com/AstraaDev/Discord-FarmMergeValley-Injector) - Spawn an upgrade card.
* [x] \- [spawnBubbledObject](https://github.com/AstraaDev/Discord-FarmMergeValley-Injector) - Spawn a bubble object *(gifts, coins, gems, energy, crates, chests, keys, decorations)*.
* [x] \- [removeAllObstacles](https://github.com/AstraaDev/Discord-FarmMergeValley-Injector) - Remove all obstacles *(trees and stones)* from the map.
* [x] \- [setLuckyMergeChance](https://github.com/AstraaDev/Discord-FarmMergeValley-Injector) - Set the lucky merge chance of objects.

---

## Common Steps for Each Method

All methods rely on pausing the game at a precise moment to access normally restricted elements. The difference between methods lies in the specific data retrieved, the exact breakpoint timing, and the injection commands. The initial setup is the same for all methods.

* Launch Farm Merge Valley on Discord and **do not close it** until you finish.
* Open the browser DevTools *(press `CTRL` + `SHIFT` + `I` on Windows/Linux or `Cmd` + `Opt` + `I` on Mac)*.
* The game should now be paused. In the **CONSOLE** tab, enter:
```js
Function.prototype.constructor = function() {};
```

* Click the **Resume script execution** button *(the blue ▶️ button) (see image below)*
<img src="img/readme_screenshot/FMV_1.png" width="100">

Make sure these steps are followed exactly before proceeding to any method-specific instruction

---

## \[METHOD 1] : giveInventoryItem

<details>
<summary>Items you can obtain with this method</summary>

| Parameter     | Description           |
| :------------ | :-------------------- |
| `coins`       | Yellow coins          |
| `gems`        | Purple gems           |
| `exp`         | Experience            |
| `level`       | Level                 |
| `crates`      | Crates with items     |
| `energy`      | Energy for activities |
| `tickets`     | Train tickets         |
| `wheat`       | Wheat                 |
| `egg`         | Egg                   |
| `sunflower`   | Sunflower             |
| `milk`        | Milk                  |
| `sugarcane`   | Sugarcane             |
| `bacon`       | Bacon                 |
| `carrot`      | Carrot                |
| `goatmilk`    | Goat milk             |
| `soybeans`    | Soybeans              |
| `wool`        | Wool                  |
| `corn`        | Corn                  |
| `fur`         | Fur                   |
| `coffeebeans` | Coffee beans          |
| `tomato`      | Tomato                |
| `avocado`     | Avocado               |
| `truffle`     | Truffle               |

</details>

<details>
<summary>Click to expand detailed instructions</summary>

#### Locating the File
* Go to the **SOURCE** tab.
* Open the file search panel *(`CTRL`+`P`)*.
* Search for the file `AutoPlaceSystem.ts`.

> **Note:** Full path:
> `/farm-merge-game/src/core/gameobjects/systems/AutoPlaceSystem.ts`

#### Injection
* Inside `AutoPlaceSystem.ts`, open the search panel *(`CTRL`+`F`)*.
* Search for:
```ts
const originCell
```

* There will be only **one result**. Set a **breakpoint** on this line by clicking in the gray area to the left.
<img src="img/readme_screenshot/FMV_3.png" width="400">  

> **Full line:**
> `const originCell: GridCell | undefined = this.services.mapGrid.getCell(autoPlaceBehavior.rootPosition.column, autoPlaceBehavior.rootPosition.row);`

* Return to the game and **move an object** *(or place it on another object)*. The game should pause again.
* In the **CONSOLE** tab, enter:
```js
worldServices = this.services
```

* Go back to the `AutoPlaceSystem.ts` file in the **SOURCE** tab, remove the breakpoint *(click it again)*, then click `Resume script execution`.

#### Setting up the function
* In the **CONSOLE**, enter:
```js
let giveInventoryItem = (target, amount) => {
    return worldServices.rewardService.giveInventoryReward({
        "reward": {"key": target, "amount": amount},
        "parent": worldServices.mapGridView._view.parent.parent.parent
    });
}
```

#### Using the Injection
* Now, in the **CONSOLE**, run:
```js
giveInventoryItem("item", amount);
```

Replace `"item"` with one of the parameters from the table above, and `amount` with your desired quantity.

</details>

---

## \[METHOD 2] : spawnUpgradeCard

<details>
<summary>Click to expand detailed instructions</summary>

#### Locating the File
* Go to the **SOURCE** tab.
* Open the file search panel *(`CTRL`+`P`)*.
* Search for the file `AutoPlaceSystem.ts`.

> **Note:** Full path:
> `/farm-merge-game/src/core/gameobjects/systems/AutoPlaceSystem.ts`

#### Injection
* Inside `AutoPlaceSystem.ts`, open the search panel *(`CTRL`+`F`)*.
* Search for:
```js
['_forc' + 'edLoo' + 't'] = []
```

 Set a **breakpoint** on this line by clicking in the gray area to the left.
<img src="img/readme_screenshot/FMV_6.png" width="300">

* Return to the game and merge three objects *(e.g., eggs or wheat)*. The game will pause only if you merge tier 3 objects.
* In the **SOURCE** tab, locate the loot array at `Local/this/_data/loot`.
<img src="img/readme_screenshot/FMV_4.png" width="300">

* Replace one element with `"upgrade_card_1"`, `"upgrade_card_2"`, or `"upgrade_card_3"` depending on your needs.
<img src="img/readme_screenshot/FMV_5.png" width="300">

* Go back to `main.js` in **SOURCE**, remove the breakpoint, then click `Resume script execution`.
* Click the merged item in-game; the upgrade card will spawn.

</details>

---

## [METHOD 3] : spawnBubbledObject

<details>
<summary>Items you can obtain with this method</summary>

### Consumable

| Parameter                         | Description                      | Image                                                                                    |
| :-------------------------------- | :------------------------------- | :--------------------------------------------------------------------------------------- |
| `ticket`                          | Ticket                           | <img src="img/game_objects/consumable/ticket.png" width="50" />                          |
| `coin_1`                          | Coins (up to coin_8)             | <img src="img/game_objects/consumable/coin_1.png" width="50" />                          |
| `gem_1`                           | Gems (up to gem_6)               | <img src="img/game_objects/consumable/gem_1.png" width="50" />                           |
| `crate_1`                         | Crates (up to crate_2)           | <img src="img/game_objects/consumable/crate_1.png" width="50" />                         |
| `energy_1`                        | Energy (up to energy_4)          | <img src="img/game_objects/consumable/energy_1.png" width="50" />                        |
| `wood_1`                          | Wood (up to wood_8)              | <img src="img/game_objects/consumable/wood_1.png" width="50" />                          |
| `stone_1`                         | Stone (up to stone_8)            | <img src="img/game_objects/consumable/stone_1.png" width="50" />                         |
| `tool_1`                          | Tool (up to tool_10)             | <img src="img/game_objects/consumable/tool_1.png" width="50" />                          |
| `flower_1`                        | Flower (up to flower_10)         | <img src="img/game_objects/consumable/flower_1.png" width="50" />                        |
| `sapling_1`                       | Sapling (up to sapling_3)        | <img src="img/game_objects/consumable/sapling_1.png" width="50" />                       |
| `greenhouse_1`                    | Greenhouse (up to greenhouse_12) | <img src="img/game_objects/consumable/greenhouse_1.png" width="50" />                    |
| `toolbox_small`                   | Small toolbox                    | <img src="img/game_objects/consumable/toolbox_small.png" width="50" />                   |
| `toolbox_medium`                  | Medium toolbox                   | <img src="img/game_objects/consumable/toolbox_medium.png" width="50" />                  |
| `toolbox_large`                   | Large toolbox                    | <img src="img/game_objects/consumable/toolbox_large.png" width="50" />                   |
| `rock_small`                      | Small rock                       | <img src="img/game_objects/consumable/rock_small.png" width="50" />                      |
| `rock_medium`                     | Medium rock                      | <img src="img/game_objects/consumable/rock_medium.png" width="50" />                     |
| `rock_large`                      | Large rock                       | <img src="img/game_objects/consumable/rock_large.png" width="50" />                      |
| `tree_small`                      | Small tree                       | <img src="img/game_objects/consumable/tree_small.png" width="50" />                      |
| `tree_medium`                     | Medium tree                      | <img src="img/game_objects/consumable/tree_medium.png" width="50" />                     |
| `tree_large`                      | Large tree                       | <img src="img/game_objects/consumable/tree_large.png" width="50" />                      |
| `reward_crate_daily_bonus`        | Daily bonus gift                 | <img src="img/game_objects/consumable/reward_crate_daily_bonus.png" width="50" />        |
| `reward_crate_key_bronze`         | Bronze key                       | <img src="img/game_objects/consumable/reward_key_bronze.png" width="50" />               |
| `reward_crate_key_silver`         | Silver key                       | <img src="img/game_objects/consumable/reward_key_silver.png" width="50" />               |
| `reward_crate_key_gold`           | Gold key                         | <img src="img/game_objects/consumable/reward_key_gold.png" width="50" />                 |
| `reward_crate_bronze`             | Bronze chest                     | <img src="img/game_objects/consumable/reward_crate_chest_bronze.png" width="50" />       |
| `reward_crate_silver`             | Silver chest                     | <img src="img/game_objects/consumable/reward_crate_chest_silver.png" width="50" />       |
| `reward_crate_gold`               | Gold chest                       | <img src="img/game_objects/consumable/reward_crate_chest_gold.png" width="50" />         |
| `golden_carrot`                   | Golden carrot                    | <img src="img/game_objects/consumable/golden_carrot.png" width="50" />                   |
| `reward_crate_key_golden_carrot`  | Golden carrot key                | <img src="img/game_objects/consumable/reward_crate_key_golden_carrot.png" width="50" />  |
| `reward_crate_golden_carrot`      | Golden carrot chest              | <img src="img/game_objects/consumable/reward_crate_golden_carrot.png" width="50" />      |
| `golden_pumpkin`                  | Golden pumpkin                   | <img src="img/game_objects/consumable/golden_pumpkin.png" width="50" />                  |
| `reward_crate_key_golden_pumpkin` | Golden pumpkin key               | <img src="img/game_objects/consumable/reward_crate_key_golden_pumpkin.png" width="50" /> |
| `reward_crate_golden_pumpkin`     | Golden pumpkin chest             | <img src="img/game_objects/consumable/reward_crate_golden_pumpkin.png" width="50" />     |
| `reward_crate_key_jingleballs`    | Jingleballs key                  | <img src="img/game_objects/consumable/reward_crate_key_jingleballs.png" width="50" />    |
| `reward_crate_jingleballs`        | Jingleballs chest                | <img src="img/game_objects/consumable/reward_crate_jingleballs.png" width="50" />        |


### Decoration
#### Farm

| Parameter                   | Description     | Image                                                                                       |
| :-------------------------- | :-------------- | :------------------------------------------------------------------------------------------ |
| `decorative_barn`           | Barn            | <img src="img/game_objects/decoration/farm/decorative_barn.png" width="100" />              |
| `decorative_birdshouse`     | Birdshouse      | <img src="img/game_objects/decoration/farm/decorative_birdshouse.png" width="100" />        |
| `decorative_chickencoop`    | Chickencoop     | <img src="img/game_objects/decoration/farm/decorative_chickencoop.png" width="100" />       |
| `decorative_doghouse`       | Doghouse        | <img src="img/game_objects/decoration/farm/decorative_doghouse.png" width="100" />          |
| `decorative_farmhouse`      | Farmhouse       | <img src="img/game_objects/decoration/farm/decorative_farmhouse.png" width="100" />         |
| `decorative_feedingtrough`  | Feeding Trough  | <img src="img/game_objects/decoration/farm/decorative_feedingtrough.png" width="100" />     |
| `decorative_flowerpots`     | Flowerpots      | <img src="img/game_objects/decoration/farm/decorative_flowerpots.png" width="100" />        |
| `decorative_fountain`       | Fountain        | <img src="img/game_objects/decoration/farm/decorative_fountain.png" width="100" />          |
| `decorative_haywagon`       | Haywagon        | <img src="img/game_objects/decoration/farm/decorative_haywagon.png" width="100" />          |
| `decorative_lamppost`       | Lamppost        | <img src="img/game_objects/decoration/farm/decorative_lamppost.png" width="100" />          |
| `decorative_milktank`       | Milktank        | <img src="img/game_objects/decoration/farm/decorative_milktank.png" width="100" />          |
| `decorative_picknicktable`  | Picnic Table    | <img src="img/game_objects/decoration/farm/decorative_picknicktable.png" width="100" />     |
| `decorative_shed`           | Shed            | <img src="img/game_objects/decoration/farm/decorative_shed.png" width="100" />              |
| `decorative_silo`           | Silo            | <img src="img/game_objects/decoration/farm/decorative_silo.png" width="100" />              |
| `decorative_stoneflowerpot` | Stone Flowerpot | <img src="img/game_objects/decoration/farm/decorative_stoneflowerpot.png" width="100" />    |
| `decorative_toilet`         | Toilet          | <img src="img/game_objects/decoration/farm/decorative_toilet.png" width="100" />            |
| `decorative_watertower`     | Water Tower     | <img src="img/game_objects/decoration/farm/decorative_watertower.png" width="100" />        |
| `decorative_well`           | Well            | <img src="img/game_objects/decoration/farm/decorative_well.png" width="100" />              |
| `decorative_windmill`       | Windmill        | <img src="img/game_objects/decoration/farm/decorative_windmill.png" width="100" />          |

#### Halloween

| Parameter                              | Description         | Image                                                                                                        |
| :------------------------------------- | :------------------ | :----------------------------------------------------------------------------------------------------------- |
| `decorative_halloween_blackcat`        | BlackCat            | <img src="img/game_objects/decoration/halloween/decorative_halloween_blackcat.png" width="100" />            |
| `decorative_halloween_cauldron`        | Cauldron            | <img src="img/game_objects/decoration/halloween/decorative_halloween_cauldron.png" width="100" />            |
| `decorative_halloween_ghosts`          | Ghosts              | <img src="img/game_objects/decoration/halloween/decorative_halloween_ghosts.png" width="100" />              |
| `decorative_halloween_grandfatherclock`| Grandfather Clock   | <img src="img/game_objects/decoration/halloween/decorative_halloween_grandfatherclock.png" width="100" />    |
| `decorative_halloween_grave01`         | Grave 01            | <img src="img/game_objects/decoration/halloween/decorative_halloween_grave01.png" width="100" />             |
| `decorative_halloween_grave02`         | Grave 02            | <img src="img/game_objects/decoration/halloween/decorative_halloween_grave02.png" width="100" />             |
| `decorative_halloween_graveyard`       | Graveyard           | <img src="img/game_objects/decoration/halloween/decorative_halloween_graveyard.png" width="100" />           |
| `decorative_halloween_hauntedhouse`    | Haunted House       | <img src="img/game_objects/decoration/halloween/decorative_halloween_hauntedhouse.png" width="100" />        |
| `decorative_halloween_pumpkinpatchbig` | Pumpkin Patch (Big) | <img src="img/game_objects/decoration/halloween/decorative_halloween_pumpkinpatchbig.png" width="100" />     |
| `decorative_halloween_pumpkins01`      | Pumpkins 01         | <img src="img/game_objects/decoration/halloween/decorative_halloween_pumpkins01.png" width="100" />          |
| `decorative_halloween_pumpkins02`      | Pumpkins 02         | <img src="img/game_objects/decoration/halloween/decorative_halloween_pumpkins02.png" width="100" />          |
| `decorative_halloween_pumpkins03`      | Pumpkins 03         | <img src="img/game_objects/decoration/halloween/decorative_halloween_pumpkins03.png" width="100" />          |
| `decorative_halloween_pumpkins04`      | Pumpkins 04         | <img src="img/game_objects/decoration/halloween/decorative_halloween_pumpkins04.png" width="100" />          |
| `decorative_halloween_skeletonbench`   | Skeleton Bench      | <img src="img/game_objects/decoration/halloween/decorative_halloween_skeletonbench.png" width="100" />       |
| `decorative_halloween_skeletoncarousel`| Skeleton Carousel   | <img src="img/game_objects/decoration/halloween/decorative_halloween_skeletoncarousel.png" width="100" />    |
| `decorative_halloween_skeletonpicnic`  | Skeleton Picnic     | <img src="img/game_objects/decoration/halloween/decorative_halloween_skeletonpicnic.png" width="100" />      |
| `decorative_halloween_skullaltar`      | Skull Altar         | <img src="img/game_objects/decoration/halloween/decorative_halloween_skullaltar.png" width="100" />          |
| `decorative_halloween_treeface`        | Tree Face           | <img src="img/game_objects/decoration/halloween/decorative_halloween_treeface.png" width="100" />            |
| `decorative_halloween_well`            | Well                | <img src="img/game_objects/decoration/halloween/decorative_halloween_well.png" width="100" />                |

#### Christmas

| Parameter                                    | Description           | Image                                                                                                                               |
| :------------------------------------------- | :-------------------- | :---------------------------------------------------------------------------------------------------------------------------------- |
| `decorative_christmas_candygate`             | CandyGate             | <img src="img/game_objects/decoration/christmas/decorative_christmas_candygate.png" width="100" />                                  |
| `decorative_christmas_elfmail`               | ElfMail               | <img src="img/game_objects/decoration/christmas/decorative_christmas_elfmail.png" width="100" />                                    |
| `decorative_christmas_elfteddy`              | ElfTeddy              | <img src="img/game_objects/decoration/christmas/decorative_christmas_elfteddy.png" width="100" />                                   |
| `decorative_christmas_elftrain`              | ElfTrain              | <img src="img/game_objects/decoration/christmas/decorative_christmas_elftrain.png" width="100" />                                   |
| `decorative_christmas_fireplace`             | Fireplace             | <img src="img/game_objects/decoration/christmas/decorative_christmas_fireplace.png" width="100" />                                  |
| `decorative_christmas_gift01`                | Gift 01               | <img src="img/game_objects/decoration/christmas/decorative_christmas_gift01.png" width="100" />                                     |
| `decorative_christmas_gift02`                | Gift 02               | <img src="img/game_objects/decoration/christmas/decorative_christmas_gift02.png" width="100" />                                     |
| `decorative_christmas_gift03`                | Gift 03               | <img src="img/game_objects/decoration/christmas/decorative_christmas_gift03.png" width="100" />                                     |
| `decorative_christmas_gingerbell`            | Gingerbell            | <img src="img/game_objects/decoration/christmas/decorative_christmas_gingerbell.png" width="100" />                                 |
| `decorative_christmas_gingerbreadhouse`      | GingerbreadHouse      | <img src="img/game_objects/decoration/christmas/decorative_christmas_gingerbreadhouse.png" width="100" />                           |
| `decorative_christmas_gingerbreadhousesmall` | GingerbreadHouseSmall | <img src="img/game_objects/decoration/christmas/decorative_christmas_gingerbreadhousesmall.png" width="100" />                      |
| `decorative_christmas_gingerbreadsnow`       | GingerbreadSnow       | <img src="img/game_objects/decoration/christmas/decorative_christmas_gingerbreadsnow.png" width="100" />                            |
| `decorative_christmas_nutcracker`            | Nutcracker            | <img src="img/game_objects/decoration/christmas/decorative_christmas_nutcracker.png" width="100" />                                 |
| `decorative_christmas_santagift`             | SantaGift             | <img src="img/game_objects/decoration/christmas/decorative_christmas_santagift.png" width="100" />                                  |
| `decorative_christmas_santamail`             | SantaMail             | <img src="img/game_objects/decoration/christmas/decorative_christmas_santamail.png" width="100" />                                  |
| `decorative_christmas_sleigh`                | Sleigh                | <img src="img/game_objects/decoration/christmas/decorative_christmas_sleigh.png" width="100" />                                     |
| `decorative_christmas_snowcaroling`          | SnowCaroling          | <img src="img/game_objects/decoration/christmas/decorative_christmas_snowcaroling.png" width="100" />                               |
| `decorative_christmas_snowdinner`            | SnowDinner            | <img src="img/game_objects/decoration/christmas/decorative_christmas_snowdinner.png" width="100" />                                 |
| `decorative_christmas_snowfight`             | SnowFight             | <img src="img/game_objects/decoration/christmas/decorative_christmas_snowfight.png" width="100" />                                  |
| `decorative_christmas_snowgifting`           | SnowGifting           | <img src="img/game_objects/decoration/christmas/decorative_christmas_snowgifting.png" width="100" />                                |
| `decorative_christmas_snowglobe`             | SnowGlobe             | <img src="img/game_objects/decoration/christmas/decorative_christmas_snowglobe.png" width="100" />                                  |
| `decorative_christmas_snowjello`             | SnowJello             | <img src="img/game_objects/decoration/christmas/decorative_christmas_snowjello.png" width="100" />                                  |
| `decorative_christmas_snowlantern`           | SnowLantern           | <img src="img/game_objects/decoration/christmas/decorative_christmas_snowlantern.png" width="100" />                                |
| `decorative_christmas_snowreindeer`          | SnowReindeer          | <img src="img/game_objects/decoration/christmas/decorative_christmas_snowreindeer.png" width="100" />                               |
| `decorative_christmas_snowtelescope`         | SnowTelescope         | <img src="img/game_objects/decoration/christmas/decorative_christmas_snowtelescope.png" width="100" />                              |
| `decorative_christmas_treebig`               | TreeBig               | <img src="img/game_objects/decoration/christmas/decorative_christmas_treebig.png" width="100" />                                    |
| `golden_christmas_tree_1`                    | GoldenTree 1          | <img src="img/game_objects/decoration/christmas/golden_christmas_tree_1.png" width="100" />                                         |
| `golden_christmas_tree_2`                    | GoldenTree 2          | <img src="img/game_objects/decoration/christmas/golden_christmas_tree_2.png" width="100" />                                         |
| `golden_christmas_tree_3`                    | GoldenTree 3          | <img src="img/game_objects/decoration/christmas/golden_christmas_tree_3.png" width="100" />                                         |
| `golden_christmas_tree_4`                    | GoldenTree 4          | <img src="img/game_objects/decoration/christmas/golden_christmas_tree_4.png" width="100" />                                         |
| `golden_jingleball_1`                        | GoldenJingleBall 1    | <img src="img/game_objects/decoration/christmas/golden_jingleball_1.png" width="100" />                                             |
| `golden_jingleball_2`                        | GoldenJingleBall 2    | <img src="img/game_objects/decoration/christmas/golden_jingleball_2.png" width="100" />                                             |
| `golden_jingleball_3`                        | GoldenJingleBall 3    | <img src="img/game_objects/decoration/christmas/golden_jingleball_3.png" width="100" />                                             |
| `golden_jingleball_4`                        | GoldenJingleBall 4    | <img src="img/game_objects/decoration/christmas/golden_jingleball_4.png" width="100" />                                             |
</details>

<details>
<summary>Click to expand detailed instructions</summary>

#### Locating the File
* Go to the **SOURCE** tab.
* Open the file search panel *(`CTRL`+`P`)*.
* Search for the file `AutoPlaceSystem.ts`.

> **Note:** Full path:
> `/farm-merge-game/src/core/gameobjects/systems/AutoPlaceSystem.ts`

#### Injection
* Inside `AutoPlaceSystem.ts`, open the search panel *(`CTRL`+`F`)*.
* Search for:
```ts
const originCell
```

* There will be only **one result**. Set a **breakpoint** on this line by clicking in the gray area to the left.
<img src="img/readme_screenshot/FMV_3.png" width="400">  

> **Full line:**
> `const originCell: GridCell | undefined = this.services.mapGrid.getCell(autoPlaceBehavior.rootPosition.column, autoPlaceBehavior.rootPosition.row);`

* Return to the game and **move an object** *(or place it on another object)*. The game should pause again.
* In the **CONSOLE** tab, enter:
```js
worldServices = this.services
```

* Go back to the `AutoPlaceSystem.ts` file in the **SOURCE** tab, remove the breakpoint *(click it again)*, then click `Resume script execution`.

#### Setting up the function
* In the **CONSOLE**, enter:
```js
let spawnBubbledObject = (target) => {
    return worldServices.rewardService.giveObjectReward({
      "rewards": [target],
      "container": worldServices.mapGridView._view.parent.parent.parent,
      "animationEndEvent": null,
      "bubblePosition": {"x": 0, "y": -200}
    });
}
```

#### Using the Injection
* Now run in the **CONSOLE**:
```js
spawnBubbledObject("item");
```

Replace `"item"` with the desired object key.

</details>

---

## \[METHOD 4] : removeAllObstacles

<details>
<summary>Click to expand detailed instructions</summary>

#### Locating the File
* Go to the **SOURCE** tab.
* Open the file search panel *(`CTRL`+`P`)*.
* Search for the file `AutoPlaceSystem.ts`.

> **Note:** Full path:
> `/farm-merge-game/src/core/gameobjects/systems/AutoPlaceSystem.ts`

#### Injection
* Inside `AutoPlaceSystem.ts`, open the search panel *(`CTRL`+`F`)*.
* Search for:
```ts
const originCell
```

* There will be only **one result**. Set a **breakpoint** on this line by clicking in the gray area to the left.
<img src="img/readme_screenshot/FMV_3.png" width="400">  

> **Full line:**
> `const originCell: GridCell | undefined = this.services.mapGrid.getCell(autoPlaceBehavior.rootPosition.column, autoPlaceBehavior.rootPosition.row);`

* Return to the game and **move an object** *(or place it on another object)*. The game should pause again.
* In the **CONSOLE** tab, enter:
```js
worldServices = this.services
```

* Go back to the `AutoPlaceSystem.ts` file in the **SOURCE** tab, remove the breakpoint *(click it again)*, then click `Resume script execution`.

#### Setting up the function
* In the **CONSOLE**, enter:
```js
worldServices = this.services
```

* Return to `AutoPlaceSystem.ts`, remove the breakpoint, then resume execution.

#### Using the Injection
* In the **CONSOLE**, run:
```js
worldServices.world.getAllGameObjects()
  .filter(x => x.hasBehavior("hitpoints") && !x.hasBehavior("shovelable") && !x.hasBehavior("movable"))
  .forEach(x => worldServices.world.removeGameObject(x))
```

</details>

---

## \[METHOD 5] : setLuckyMergeChance

<details>
<summary>Click to expand detailed instructions</summary>

#### Locating the File
* Go to the **SOURCE** tab.
* Open the file search panel *(`CTRL`+`P`)*.
* Search for the file `AutoPlaceSystem.ts`.

> **Note:** Full path:
> `/farm-merge-game/src/core/gameobjects/systems/AutoPlaceSystem.ts`

#### Injection
* Inside `AutoPlaceSystem.ts`, open the search panel *(`CTRL`+`F`)*.
* Search for:
```ts
const originCell
```

* There will be only **one result**. Set a **breakpoint** on this line by clicking in the gray area to the left.
<img src="img/readme_screenshot/FMV_3.png" width="400">  

> **Full line:**
> `const originCell: GridCell | undefined = this.services.mapGrid.getCell(autoPlaceBehavior.rootPosition.column, autoPlaceBehavior.rootPosition.row);`

* Return to the game and **move an object** *(or place it on another object)*. The game should pause again.
* In the **CONSOLE** tab, enter:
```js
worldServices = this.services
```

* Go back to the `AutoPlaceSystem.ts` file in the **SOURCE** tab, remove the breakpoint *(click it again)*, then click `Resume script execution`.

#### Setting up the function
* In the **CONSOLE**, enter:
```js
let setLuckyMergeChance = (percentage) => worldServices.mapGridView._view.parent.parent.parent._systems.find(x => x._luckyMergeChance)._luckyMergeChance = percentage;
```

#### Using the Injection
* Run in the **CONSOLE**:
```js
setLuckyMergeChance(percentage);
```

Replace `percentage` with a number between 0 and 100.

* `100` means the lucky merge always happens.
* `0` means it never happens *(default is 5)*.

</details>

---

## Additional Information

* Changes to XP Level won't update on-screen until you exit and relaunch FMV. However, effects like unlocking new plots apply immediately.
* Using negative values for level will reduce XP Level; similarly, negative amounts for resources will remove them.
* Be aware that FMV will become unstable/unplayable if XP Level exceeds 70 *(FMV v1.62.6)*. You can reduce level by adding negative values to fix this. *(See [issue 7](https://github.com/AstraaDev/FarmMergeValley-Injector/issues/7))*
* Need help? Join the [Discord Server](https://astraadev.github.io/#/discord).
* Contributions welcome! Open issues or create pull requests.
