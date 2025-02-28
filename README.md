<p align="center">
  <img src="https://venturebeat.com/wp-content/uploads/2022/11/press_release_banner.jpg" width="800">
</p>

<h1 align="center">[Discord] - FarmMergeValley Injector</h1>

<p align="left">
  FMV Injector lets you set up various methods for modifying content in the Farm Merge Valley discord game. This project follows on from @wooslow's repositorie on the same subject. Perform these steps preferably from a Google Chrome browser. There is currently no guarantee that these methods will work on other browsers.
  These methods go against the rules of the game's developers, and waves of bans have already occurred. I am in no way responsible for your actions. Please use this tool with full knowledge of the risks involved.
</p>

---

## Features

- [x] - [giveInventoryItem](https://github.com/AstraaDev/Discord-FarmMergeValley-Injector) - Obtain any object in unlimited quantities.
- [x] - [spawnUpgradeCard](https://github.com/AstraaDev/Discord-FarmMergeValley-Injector) - Spawn an upgrade card.
- [x] - [spawnBubbledObject](https://github.com/AstraaDev/Discord-FarmMergeValley-Injector) - Spawn a bubble object (gift, coins, gems, energy, crates, chests, keys, decorations).
- [x] - [removeAllObstacles](https://github.com/AstraaDev/Discord-FarmMergeValley-Injector) - remove all obstacles (trees and stones) from the map.
- [x] - [setLuckyMergeChance](https://github.com/AstraaDev/Discord-FarmMergeValley-Injector) - Set the lucky merge chance of objects.

---

## Common part of each method
Each of the methods described here works in the same way. The game needs to be “paused” at the right moment to access certain elements that are normally blocked. The differences between these methods are the information to be retrieved, the precise moment to break the script, the action to be taken to break the script, etc...
Even if these parts change depending on the method, the beginning remains the same.

---

#### Setup
- Launch of Farm Merge Valley on discord *(and never close it again until the end)*
- Open the browser console (by pressing `CTRL`+`SHIFT`+`I` on Windows/Linux or `Cmd`+`Opt`+`I` on MacOS)
- Your game should now be "paused". In the **CONSOLE** tab, write the following command and press `ENTER` :
```js
Function.prototype.constructor = function() {};
```
- Click on the `Resume script execution` button *(see image below) (it's the blue button)*
<img src="img/readme_screenshot/FMV_1.png" width="100">

- In the **SOURCE** tab, find the file named main.js located at `top/1187.discordsays.com/1187.discordsays.com/main.1401.js` *(see image below)*
<img src="img/readme_screenshot/FMV_2.png" width="300">

From now on, the next steps will depend on each method. Make sure you've followed exactly the steps described in this section before moving on.

---

## [METHOD 1] : giveInventoryItem
<details>
<summary>What you can get with this method ?</summary>
  
| Parameter       | Description           |
| :-------------- | :-------------------- |
| `coins`         | Yellow coins          |
| `gems`          | Purple gems           |
| `exp`           | Experience            |
| `levels`        | Levels                |
| `crates`        | Crates with items     |
| `energy`        | Energy for activities |
| `tickets`       | Train tickets         |
| `wheat`         | Wheat                 |
| `egg`           | Egg                   |
| `sunflower`     | Sunflower             |
| `milk`          | Milk                  |
| `sugarcane`     | Sugarcane             |
| `bacon`         | Bacon                 |
| `carrot`        | Carrot                |
| `goatmilk`      | Goat milk             |
| `soybeans`      | Soybeans              |
| `wool`          | Wool                  |
| `corn`          | Corn                  |
| `fur`           | Fur                   |
| `coffeebeans`   | Coffee beans          |
| `tomato`        | Tomato                |
| `avocado`       | Avocado               |
| `truffle`       | Truffle               |
</details>

<details>
<summary>Click to expand the information</summary>

Make sure you've followed exactly the steps described in the “Common part of each method” section before moving on to this one.

#### Injection
- In `main.js` file,
- Search the file (by pressing `CTRL`+`F`)
- Write the following command and press `ENTER` :
```js
this['servi' + 'ces']['mapGr' + 'id']['getCe' + 'll']
```
- There will normally be 9 results. Navigate to the 2nd result and set a breakpoint by clicking on the left of the line in the grey area *(see image below)*
<img src="img/readme_screenshot/FMV_3.png" width="400">

- Return to the game and moove an object *(the game should stop again)*
- In the **CONSOLE** tab, write the following command and press `ENTER` :
```js
worldServices = this.services
```
- You can now go back to the `main.js` file in the **SOURCE** tab, then remove the breakpoint *(by clicking on it again)* and click on the `Resume script execution` button again

#### Setting up the function
- In the **CONSOLE** tab, write the following command and press `ENTER` :
```js
let giveInventoryItem = (target, amount) => {
    return worldServices.rewardService.giveInventoryReward({
        "reward": {"key": target, "amount": amount},
        "parent": worldServices.mapGridView._view.parent.parent.parent
    });
}
```

#### Use injection
You're all set! Now all you have to do is enter the following command in the **CONSOLE** tab and press `ENTER` :
```js
giveInventoryItem("item", amount);
```
Don't forget to replace the `item` argument with one of the parameters in the `What you can get with this method?` table of this method, and `amount` with the amount you want.
</details>

---

## [METHOD 2] : spawnUpgradeCard
<details>
<summary>Click to expand the information</summary>
Make sure you've followed exactly the steps described in the “Common part of each method” section before moving on to this one.
  
#### Injection
- In `main.js` file,
- Search the file (by pressing `CTRL`+`F`)
- Write the following command and press `ENTER` :
```js
['_forc' + 'edLoo' + 't'] = []
```
- Set a breakpoint by clicking on the left of the line in the grey area *(see image below)*
<img src="img/readme_screenshot/FMV_6.png" width="300">

- - Return to the game and merge three objects (e.g. eggs, wheat). The game will only stop if the fusion creates an object of max evolution level. *(the game should stop again)*
- In the **SOURCE** tab, find the loot section at `Local/this/_data/loot` *(see image below)*
<img src="img/readme_screenshot/FMV_4.png" width="300">

- Replace one of the elements with `“upgrade_card_1”`, `“upgrade_card_2”` or `“upgrade_card_3”` to suit your needs *(see image below)*
<img src="img/readme_screenshot/FMV_5.png" width="300">

- You can now go back to the `main.js` file in the **SOURCE** tab, then remove the breakpoint *(by clicking on it again)* and click on the `Resume script execution` button again
- All you have to do now is click on the merged item in the game, and the upgrade card should appear.

</details>

---

## [METHOD 3] : spawnBubbledObject
<details>
<summary>What you can get with this method ?</summary>

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
<summary>Click to expand the information</summary>

Make sure you've followed exactly the steps described in the “Common part of each method” section before moving on to this one.

#### Injection
- In `main.js` file,
- Search the file (by pressing `CTRL`+`F`)
- Write the following command and press `ENTER` :
```js
this['servi' + 'ces']['mapGr' + 'id']['getCe' + 'll']
```
- There will normally be 9 results. Navigate to the 2nd result and set a breakpoint by clicking on the left of the line in the grey area *(see image below)*
<img src="img/readme_screenshot/FMV_3.png" width="400">

- Return to the game and moove an object *(the game should stop again)*
- In the **CONSOLE** tab, write the following command and press `ENTER` :
```js
worldServices = this.services
```
- You can now go back to the `main.js` file in the **SOURCE** tab, then remove the breakpoint *(by clicking on it again)* and click on the `Resume script execution` button again

#### Setting up the function
- In the **CONSOLE** tab, write the following command and press `ENTER` :
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

#### Use injection
You're all set! Now all you have to do is enter the following command in the **CONSOLE** tab and press `ENTER` :
```js
spawnBubbledObject("item");
```
Don't forget to replace the `item` argument with one of the parameters in the `What you can get with this method?` table of this method.
</details>

---

## [METHOD 4] : removeAllObstacles
<details>
<summary>Click to expand the information</summary>
Make sure you've followed exactly the steps described in the “Common part of each method” section before moving on to this one.

#### Injection
- In `main.js` file,
- Search the file (by pressing `CTRL`+`F`)
- Write the following command and press `ENTER` :
```js
this['servi' + 'ces']['mapGr' + 'id']['getCe' + 'll']
```
- There will normally be 9 results. Navigate to the 2nd result and set a breakpoint by clicking on the left of the line in the grey area *(see image below)*
<img src="img/readme_screenshot/FMV_3.png" width="400">

- Return to the game and moove an object *(the game should stop again)*
- In the **CONSOLE** tab, write the following command and press `ENTER` :
```js
worldServices = this.services
```
- You can now go back to the `main.js` file in the **SOURCE** tab, then remove the breakpoint *(by clicking on it again)* and click on the `Resume script execution` button again

#### Use injection
- In the **CONSOLE** tab, write the following command and press `ENTER` :
```js
worldServices.world.getAllGameObjects().filter(x=>x.hasBehavior("hitpoints") && !x.hasBehavior("shovelable") && !x.hasBehavior("movable")).forEach(x=>worldServices.world.removeGameObject(x))
```
</details>

---

## [METHOD 5] : setLuckyMergeChance
<details>
<summary>Click to expand the information</summary>
  
Make sure you've followed exactly the steps described in the “Common part of each method” section before moving on to this one.

#### Injection
- In `main.js` file,
- Search the file (by pressing `CTRL`+`F`)
- Write the following command and press `ENTER` :
```js
this['servi' + 'ces']['mapGr' + 'id']['getCe' + 'll']
```
- There will normally be 9 results. Navigate to the 2nd result and set a breakpoint by clicking on the left of the line in the grey area *(see image below)*
<img src="img/readme_screenshot/FMV_3.png" width="400">

- Return to the game and moove an object *(the game should stop again)*
- In the **CONSOLE** tab, write the following command and press `ENTER` :
```js
worldServices = this.services
```
- You can now go back to the `main.js` file in the **SOURCE** tab, then remove the breakpoint *(by clicking on it again)* and click on the `Resume script execution` button again

#### Setting up the function
- In the **CONSOLE** tab, write the following command and press `ENTER` :
```js
let setLuckyMergeChance = (percentage) => worldServices.mapGridView._view.parent.parent.parent._systems.find(x => x._luckyMergeChance)._luckyMergeChance = percentage;
```

#### Use injection
You're all set! Now all you have to do is enter the following command in the **CONSOLE** tab and press `ENTER` :
```js
setLuckyMergeChance(percentage);
```
Don't forget to replace the `percentage` argument with a number between 0 and 100. Setting `100` as an argument means that the lucky merge will always take place, and setting `0` as an argument means that the lucky merge will never take place (the default value is 5).
</details>

## Additional Informations
Discord :
- Any question ? Any malfunction ? Contact me on [here](discord.gg/PKR7nM9j9U).
