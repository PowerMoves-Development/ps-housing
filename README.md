PowerMoves Development - ps-housing (Forked)
A modified version of ps-housing specifically adapted for the PowerMoves Development Government System.

⚠️ IMPORTANT DISCLAIMER & WARNING ⚠️
This repository contains a FORKED and MODIFIED version of the original ps-housing script. It is designed to work EXCLUSIVELY with the pm-government system developed by PowerMoves Development. We strongly advise against using this fork as a standalone replacement for your standard ps-housing script or integrating it with other non-PowerMoves Development government systems, as it contains specific database and logic changes that may cause incompatibilities or errors.

✨ Key Modifications for pm-government Integration
This fork includes essential changes to support the advanced government and taxation features planned for pm-government. The primary modifications are:

Database Schema Additions:
property_type (TEXT): A new column added to the player_houses table (or equivalent, check your specific housing script's table name). This column categorizes properties (e.g., 'residential', 'commercial', 'agricultural', 'industrial'). This value is intended to be set manually by realtors via the ps-realty script (forked by PowerMoves Development).

owner_type (TEXT): A new column added to the player_houses table. This categorizes the owning entity ('citizen', 'company', 'government'). This data is crucial for pm-government's internal management, including determining voter eligibility based on property ownership and supporting various legislative processes.

is_tax_exempt (BOOLEAN/TINYINT): A new column added to the player_houses table. This is a boolean flag (0 for false, 1 for true) indicating if a property is exempt from taxes. This field is ALWAYS set MANUALLY by a Property Assessor via the pm-government tablet, based on roleplay justification. It is NOT automatically set by owner_type or any other factor.

Lua Logic Adjustments:
Modifications within ps-housing's Lua files to correctly save, load, and manage these new database fields when properties are interacted with (e.g., bought, sold, loaded).

📝 PowerMoves Development Note on Licensing and Attribution
This script is a fork of the original ps-housing project. All original copyrights, intellectual property, and credits belong to the original authors and contributors of ps-housing. PowerMoves Development's modifications are layered on top of their foundational work.

We have maintained the original LICENSE file within this repository, which governs the usage and distribution of the original codebase. Our modifications are made in accordance with the terms of that original license.

Original Repository: [PASTE LINK TO THE ORIGINAL ps-housing GITHUB REPO HERE]

🤝 Contributing & Support
This fork is maintained by PowerMoves Development for its specific use with the pm-government system. While we appreciate interest, we are not actively seeking external contributions for this specific fork unless it's to fix critical bugs or improve pm-government compatibility.

For issues or questions related to this fork's integration with pm-government, please refer to the pm-government repository's issue tracker. For issues with the original, un-modified ps-housing functionality, please consult the original repository's issue tracker.
# ps-housing IPL & MLO Support

## Table of Contents

-   [Description](#description)
    -   [Creating a new property for sale](#creating-a-new-property-for-sale)
    -   [Furnish and decorate a property](#furnish-and-decorate-a-property)
    -   [Shell Support](#shell-support)
-   [Installation](#installation)
    -   [Important](#important)
    -   [Migrating houses/apartments](#migrating-housesapartments)
    -   [Item Limits System](#item-limits-system)
    -   [Logs System Setup](#logs-system-setup)
    -   [Adding New Shells](#adding-new-shells)
    -   [Dynamic Doors](#dynamic-doors)
-   [FAQ](#faq)
-   [Preview](#preview)
-   [Credits](#credits)

## Description

ps-housing is a resource that opens up a world of creative possibilities for housing. Its user-friendly interface lets you decorate any location to your heart's content. The best part? Not only is it completely free, but it's also reliable and functional, unlike many other housing systems available. What's included?

-   Players can decorate their houses and apartments with a full selection of furniture and decorations (included a wide variety of custom housing props)
-   Provides support for housing and apartments and is a full replacement for qb-apartments and qb-housing
    -   When a player first spawns after enabling ps-housing, they will have to choose an apartment. Once they spawn in the stashitems from their previous qb-apartment will be migrated to their new apartment stash.
-   Allows players to purchase and list houses for sale through `ps-realtor` and the realtor job
-   Houses come with personal garages
-   Houses and apartments come with personal wardrobes and stashes
-   Players can share keys to their houses and apartments with other players

### Creating a new property for sale

Players must have the realtor job to create new properties. Additionally if the realtor has a high enough grade level, they can also help players move to new apartments.
All properties must be manually configured for sale by the realtor job, giving you full control over all aspects of properties, and bringing another avenue of roleplay to your server.

-   Pick the location where you want to create a new property
-   Use `/housing` to open the housing menu
-   Click on create new property
-   Fill out the details of the property (name, price, description, which shell to use, etc)
-   Choose the door location (this is where the person will enter the house)
    -   Ensure that you place it up against a wall, since players will use target to enter the house
-   Choose the garage location
    -   This point is used both for storing vehicles, as well as the location where the vehicle will spawn when taken out of the garage
-   Realtors can edit the details of the property by clicking on the property in the housing menu
-   Players can see the properties for sale through the /housing menu as well

### Furnish and decorate a property

Once inside the property, the player can furnish and decorate the property to their liking. They can also invite other players to their property, and give them access to the property. Open the furniture store by pressing `Z`.

This will open a furniture store complete with all of the props. Select an item from the catalog and place it into the property. You can use the placement gizmo to position the item to your liking as well as use the UI tools for fine tune control over the placement. Once you are happy with the positioning, make sure you press `Add to Cart` before moving on. Continue to add as many items as you want to your cart. Once you are done, go to the `Checkout` and purchase the items.

> Note: The place on ground button sometimes does not work properly depending on where the native detects the ground to be.

### Shell Support

-   [K4MB1](https://github.com/Project-Sloth/ps-housing/wiki/K4MB1-Shells-Support-&-Offsets)

## Installation

Follow either one or the other installation guides below based on your setup:

-   [QB-core installation guide](https://github.com/Project-Sloth/ps-housing/tree/main/README%20-%20INSTALL%20INSTRUCTIONS/QBCore)
-   [Qbox installation guide](https://github.com/Project-Sloth/ps-housing/tree/main/README%20-%20INSTALL%20INSTRUCTIONS/QBOX)

Remember to install the following **dependencies** if you don't already have them:

1. [ox_lib](https://github.com/overextended/ox_lib/releases)
1. [ps-realtor](https://github.com/Project-Sloth/ps-realtor)
1. [fivem-freecam](https://github.com/Deltanic/fivem-freecam)
1. [ox_target](https://github.com/overextended/ox_target) or [qb-target](https://github.com/qbcore-framework/qb-target)

Furthermore, make sure you start the shown dependencies in the correct order as below:

```lua
-- server.cfg

ensure ox_lib
ensure ps-realtor
ensure ps-housing
ensure fivem-freecam
```

### Stashes

-   Players need to place their [stash](https://github.com/Project-Sloth/ps-housing/blob/7efd2009050b9a20969877cf69b284352a9309bf/shared/config.lua#LL426C96-L426C96) and [wardrobe](https://github.com/Project-Sloth/ps-housing/blob/7efd2009050b9a20969877cf69b284352a9309bf/shared/config.lua#L427) or else they wont have one. Check [Config](https://github.com/Project-Sloth/ps-housing/blob/7efd2009050b9a20969877cf69b284352a9309bf/shared/config.lua#L422) for more information.

This entire README is meant for compatibility with default QBCore scripts. If you have different scripts, you'll need to adjust them for compatibility yourself. Refrain from asking us how to circumvent paid scripts that can't be adjusted for ps-housing support. Instead, request their support for ps-housing - this script is fully open source for that reason. Any inquiries related to this be ignored.

### Migrating houses/apartments

1. From a client run the `migratehouses` command to automatically convert all houses from qb-houses. It will print a message to the console once complete. **The `migratehouses` command MUST be run from a client in order to retrieve street and region data for each house**

2. From a client or server console run the `migrateapartments` command to automatically convert all apartments from qb-apartments. It will print a message to the console once complete.

### Item Limits System

1. Choose an item you want to limit under `Config.Furniture` in under `shared/config.lua`
2. Add `["max"] = 3` or the number of your choice to the item (see example below)

```lua
{ ["object"] = "v_res_r_figcat", ["price"] = 300, ["max"] = 2, ["label"] = "Fig Cat" },
```

### Logs System Setup

1. Go to `qb-smallresources/server/logs.lua` and add this:

```lua
['pshousing'] = 'yourdiscordwebhookhere',
```

2. Create a webhook for the channel you want the logs to show up in.
3. Replace the placeholder with your webhook link.

> This system only supports qb-core for now.

### Adding New Shells

-   Follow the [ps-housing wiki](https://github.com/Project-Sloth/ps-housing/wiki) information.

### Dynamic Doors

Dynamic Doors will turn placed doors into actual working doors, Instead of them being static. (See videos below)

### Preview

https://github.com/complexza/ps-housing/assets/74205343/72cfc135-2f78-42b3-a540-45f02567b6d7

https://github.com/complexza/ps-housing/assets/74205343/0ff26e7f-1341-45fc-8fc6-d65421dec0b2

### Setup

-   You will need to set the `Config.DynamicDoors = true`
-   You will have to add this convar into your server.cfg `setr game_enableDynamicDoorCreation "true"`

> Note: The convar has to be in your server.cfg in order for the doors to be dynamic!

## FAQ

### Error: `Foreign key constraint is incorrectly formed`

If you come across an error such as `Foreign key constraint is incorrectly formed` while importing the `properties.sql` into your database, follow these steps to fix it.

1. Open your database in HeidiSQL.
2. Right-click on your database name and select "Edit."
3. Locate the database collation setting take a note of it.
4. You will need to format the `properties.sql` file to match your database collation.
5. Ensure that the collation of your `citizenid` column in your `players` table is `utf8mb4_general_ci` and not `utf8mb4_unicode_ci`

If your database collation is set to `utf8mb4_general_ci`, modify the last line of the `properties.sql` file using VSCode or in HeidiSQL's query tab to the following:

```sql
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```

This adjustment ensures that `properties.sql` file's character set and collation match that of your database, effectively resolving the issue.

## Preview

![image](https://github.com/Project-Sloth/ps-housing/assets/82112471/07b7f8c6-38ea-4f8c-95b6-9bd6bafbbd09)
![image](https://github.com/Project-Sloth/ps-housing/assets/82112471/163ae847-5a44-48cb-89f5-e0c1e7b59383)
![image](https://github.com/Project-Sloth/ps-housing/assets/82112471/655d9bb6-6c6d-4676-b4e0-f4368f3325a9)
![image](https://github.com/Project-Sloth/ps-housing/assets/82112471/fc632975-c2f6-41fb-89cd-a984679f1a41)

# Credits

ps-housing owes its existence to the exceptional coding expertise of [Xirvin#0985](https://github.com/ImXirvin). His application of top-tier coding practices has been instrumental in creating this script. We at Project Sloth are thrilled that he has joined our team and utilized our platform to deliver this incredible, much-anticipated resource. Our sincere appreciation goes out to [Xirvin](https://github.com/ImXirvin) for his outstanding contribution!

-   [Xirvin](https://github.com/ImXirvin)
-   [BackSH00TER](https://github.com/backsh00ter)
-   [Byte Labs Project](https://github.com/Byte-Labs-Project)
-   [Project Sloth Team](https://discord.gg/projectsloth)
-   [K4MB1](https://www.k4mb1maps.com/)
-   [Candrex](https://github.com/CandrexDev)
-   [Complexza](https://github.com/complexza)
