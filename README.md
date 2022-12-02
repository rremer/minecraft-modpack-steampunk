# minecraft-modpack-steampunk

[![Maven Central](https://img.shields.io/maven-central/v/com.github.rremer/minecraft-modpack-steampunk?versionPrefix=1.18.2-1)](https://search.maven.org/artifact/com.github.rremer/minecraft-modpack-steampunk-client/1.18.2-1/jar)
[![Docker Tag](https://img.shields.io/docker/v/rremer/minecraft-modpack-steampunk/1.18.2-1?label=docker)](https://hub.docker.com/repository/docker/rremer/minecraft-modpack-steampunk/general)
[![License](https://img.shields.io/github/license/rremer/minecraft-modpack-steampunk)](https://opensource.org/licenses/MIT)
[![Keybase PGP](https://img.shields.io/keybase/pgp/rremer)](https://keybase.io/rremer/pgp_keys.asc)

A Fabric/datapack wrapper around 'Create' mod for a more steampunk Minecraft.

## Usage

Currently, this modpack is distributed as a [MultiMC] zip.

1. If you don't have Java 17+, install it. Here's a recent build for [Windows](https://cdn.azul.com/zulu/bin/zulu17.38.21-ca-jdk17.0.5-win_x64.msi), [MacOs](https://cdn.azul.com/zulu/bin/zulu17.38.21-ca-jdk17.0.5-macosx_x64.dmg), [Linux](https://www.azul.com/downloads/?version=java-17-lts&os=linux&architecture=x86-64-bit&package=jdk)
2. [Download MultiMC] and install.
3. Open MultiMC and and add login credentials
4. Click "Add Instance" and select "Import from zip" on the left-hand side.
5. Paste in this URL: [MMC client release 1.18.2-1] and hit <Enter> 
6. When the download finishes, double-click 'minecraft-modpack-steampunk-client-1.18.2-1.zip'
7. If you are not signed into a Mojang account, you will be promted for credentials

## Features

This modpack is primarily the 'Create' mod with any theme-adjectn mods and quality-of-life features.

### Quality of Life

Here' a summary of the quality-of-life features provided by this modpack.

#### Recipe and Loot Table Fixes

Wither skeletons have a much higher chance of dropping a wither skull. Removed the recipebook and all popups (toasts) related to new recipes.

#### Gamerules

Morning starts after 25% of players online are asleep. Phantoms are disabled.

#### Just Enough Items (JEI), Just Enough Resources (JER)

Open your inventory to get a sidebar of searchable items and their recipes. Additionally see natural resources and their spawn distributions.

#### Advanced Compass

Have a normal compass, but get a compass bar in your UI with distances to mobs and custom waypoints. You start with this compass to aid early game wanderlust.

#### Nature's Compass

Locate specific biomes with this compass.

#### Gravestones

No timer to get back your stuff.

#### Lithium/Iris/Sodium/Shaderpacks

Lithium is included to speed up framerate. Iris is included along with the 'Complementary Shaders' pack, so if you want fancy current-gen graphics and lighting, you can toggle that on.

#### Emmersive Sounds and Water Effects

The Effective mod adds splashing/foaming water effects based on running water heights, as well as splashes from items or entities falling into water. Matching sound effects make the Overworld a little  more lively.

#### Fast Leaf Decay

Chopping down a tree's logs won't leave leaves in the air forever.

#### Immersive Portals

See through portals into the next dimension they go to in realtime.

### Gameplay

Here's a summary of the gameplay changes itroduced in this modpack.

#### Create

Steampunk AF. If you've played with any modpacks which introduce modded power like RF, it's that with literal bells and whistles. Rotational Power (RP) can be hand-cranked, or steam-boiled, or any number of renewable sources. Contraptions let you build massively large and moveable structures.

#### Spice Of Life: Carrot Edition

When you eat 10 new unique food items, your max health will permanently increase by 1 heart (max 30, or 3x default healthbar). Explore to find new food sources, and farm them to share the bounty with your friends.

Additionally, 'Better Statistics' is included so you can see more easily what you have and have not eaten. Go to the Menu -> Statistics, and then click through to the 'Tab: A Balanced Diet'.

#### Carpet Extra

Dispensers can place blocks, feed and milk animals, and till soil. Amethyst nodes can be pushed with pistons, along with other previously unmovable blocks like chests, dispensers, and crafting tables. Chickens can be sheared to get feathers.

#### Extra Block, Crop variants

Croptopia implements fruiting trees and vegetables into world generation, along with extra higher tier foods and kitchen crafting items to make them. Slab/stair/polished variants of many blocks are added. 'Chipped' included with specialized tables for a massive amount of texture variants on many blocks/items. A UI for zooming in on items so you can see their textures more easily when crafting.

#### Carpet Commands

For technical Minecrafters, many Carpet commands are exposed to non-operators, such as `/profile` so you can quantify how much of a burden you are on your ~~friends~~ server.


## Building

```sh
mvn clean install
```

## Server Usage

A container image is shipped to [docker.io/rremer/minecraft-modpack-steampunk]. You can start it via:
```sh
docker run -d \
  -p 25565:25565 \
  -e EULA_MINECRAFT_BOOL=true \
  -v /path/to/persistent/world:/minecraft-modpack-steampunk/.minecraft/world \
  -v /path/to/persistent/backup:/minecraft-modpack-steampunk/.minecraft/backup \
  rremer/minecraft-modpack-steampunk:1.18.2-1
```
... where ```/path/to/persistent``` is some real local filesystem to persist the world data between container restarts.


## Releasing

```sh
mvn versions:set -DnewVersion=1.18.2-1
export MAVEN_OPTS="--add-opens=java.base/java.util=ALL-UNNAMED --add-opens=java.base/java.lang.reflect=ALL-UNNAMED --add-opens=java.base/java.text=ALL-UNNAMED --add-opens=java.desktop/java.awt.font=ALL-UNNAMED"
echo 'See this bug in nexus-staging-maven-plugin for description of the above: https://issues.sonatype.org/browse/OSSRH-66257'
mvn clean deploy -Dparameter.gpg.skip=false
mvn site site-deploy
```

### Versioning

A version number of this project's artifacts is built as ```<minecraft.version>-<project.version>```, where:
* ```minecraft.version``` is a version of minecraft (1.15.2, 20w10a ...)
* ```project.version``` is an increment for this project to release against a version of minecraft (1,2,3, ...)

[MultiMC]:https://multimc.org/
[Download MultiMC]:https://multimc.org/#Download
[MMC client release 1.18.2-1]:https://repo.maven.apache.org/maven2/com/github/rremer/minecraft-modpack-steampunk-client/1.18.2-1/minecraft-modpack-steampunk-client-1.18.2-1.zip
[docker.io/rremer/minecraft-modpack-steampunk]:https://hub.docker.com/r/rremer/minecraft-modpack-steampunk/tags
