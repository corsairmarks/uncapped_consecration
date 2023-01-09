# Overview

Do you love consecrating worlds?  Do you want _more_ consecrated worlds?  Then this mod is for you!

When the game starts, you (or the host, for multiplayer) will be asked what the maximum number of consecrated worlds (per empire with the "Consecrated Worlds" ascension perk).  The game's default setting is 3, but it can be set from 1 to 10 or unlimited.  The Consecrated World Worship modifier dynamically scales based on the combined levels of all your consecrated worlds.

## Localisation

Almost all text altered by this mod is localised into eight of the languages supported by Stellaris.  However, the beginning-of-the-game event's description and "default" option are only available in English.  If you would like to supply a translation for one or more languages, please contact me via Steam or leave a comment.

# Changes

When consecrating or deconsecrating a world, the game dynamically calculates the correct bonus for Consecrated World Worship.  In order to accomplish this, it was necessary to overwrite an effect (`recalculate_consecrated_world_modifier`) and the decisions (`decision_consecrated_worlds` and `decision_unconsecrated_worlds`) as well as preempt the events (`mega.100` and `mega.110`) that deal with consecration.

The Consecrated Worlds Worship modifier is now applied via a dynamic multiplier and can now scale infinitely instead of capping out at a total of twelve "levels" of Consecrated Worlds Worship.

## Compatibility

While this mod does replace some built-in gameplay objects, it should generally play nicely with other mods as long as they do not also adjust Consecrated Worlds.

Not included in my compilation mod [Subtle Polish: A Collection of Fixes and Enhancements](https://steamcommunity.com/sharedfiles/filedetails/?id=2522974089).  This mod is compatible with the compilation.

Built for Stellaris version 3.6 "Orion."  Not compatible with achievements.

### When to Install

This mod can be safely added after the game has started and should be safe to remove.  After removing the mod, your game will revert to the built-in behavior for Consecrated Worlds (although you will not lose any if you exceed the base cap of 3).  Always backup your savegame before attempting to remove a mod.

### Known Issues

Overwriting effects and planetary decisions a well as preempting events result in the game logging error messages when first launching.  Expect to see five lines in error.log similar to these:

```
[04:30:31][game_singleobjectdatabase.h:165]: Object with key: recalculate_consecrated_world_modifier already exists, using the one at  file: common/scripted_effects/zz__uncapped_consecration_caravaneer_scripted_effects_overrides.txt line: 2
[04:30:32][eventmanager.cpp:368]: an event with id [mega.110] already exists!  file: events/megacorp_events.txt line: 12
[04:30:32][eventmanager.cpp:368]: an event with id [mega.100] already exists!  file: events/megacorp_events.txt line: 102
[04:30:33][game_singleobjectdatabase.h:165]: Object with key: decision_consecrated_worlds already exists, using the one at  file: common/decisions/03_uncapped_consecration_special_decisions_overrides.txt line: 2
[04:30:33][game_singleobjectdatabase.h:165]: Object with key: decision_unconsecrated_worlds already exists, using the one at  file: common/decisions/03_uncapped_consecration_special_decisions_overrides.txt line: 276
```

## Changelog

* 1.0.0 Initial version
* 1.1.0 Mark as compatible with Stellaris 3.2 "Herbert" - no script changes
* 2.0.0 Update for Stellaris version 3.3 "Libra"
    * Integrate updated logic for Consecrated Worlds added in version 3.3 "Libra"
    * Update decisions to cost Unity instead of Influence
* 3.0.0 Update for Stellaris version 3.4 "Cepheus" - use memory optimization feature for effects
* 4.0.0 Update for Stellaris version 3.6 "Orion" (and changes from version 3.5 "Fornax")
    * Support the new built-in consecrated world visual effects
    * You will now lose the opinion bonus for consecrated holy worlds with the spiritualist fallen empire if you lose/colonize it
* 5.0.0 Add a compatibility trigger for other mods to check whether this one is active, remove old compatibility global flag

## Source Code

Hosted on [GitHub](https://github.com/corsairmarks/uncapped_consecration)

### Development Notes

It is best to clone this repository into `<Stellaris User's Directory>/Paradox Interactive/Stellaris/mod`, and then make a connection to the `mod` folder via a `*.mod` file's `path` property.  That will ensure the game can see the files, and also that CWTools will parse them.  Also note that the README.md file exists in the `mod` directory but is symbolically linked in the root directory.