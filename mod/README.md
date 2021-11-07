# Overview

Do you love consecrating worlds?  Do you want _more_ consecrated worlds?  Then this mod is for you!

When the game starts, you (or the host, for multiplayer) will be asked what the maximum number of consecrated worlds (per empire with the "Consecrated Worlds" ascension perk).  The game's default setting is 3, but it can be set from 1 to 10 or unlimited.  The Consecrated World Worship modifier dynamically scales based on the combined levels of all your consecrated worlds.

Additionally, consecrating a world spawns the Divine Enforcer planet effects - a little graphical bonus to make the process a little prettier.  The Consecrated World modifiers now also cause planets to show their nameplates and thus be a little easier to pick them out when in the systemview.

## Localisation

Almost all text altered by this mod is localised into all eight languages supported by Stellaris.  However, the beginning-of-the-game event's description and "default" option are only available in English.  If you would like to supply a translation for one or more languages, please contact me via Steam or leave a comment.

# Changes

When consecrating or deconsecrating a world, the game dynamically calculates the correct bonus for Consecrated World Worship.  In order to accomplish this, it wa necessary to overwrite an effect (`recalculate_consecrated_world_modifier`) and the decisions (`decision_consecrated_worlds` and `decision_unconsecrated_worlds`) as well as preempt the events (`mega.100` and `mega.110`) that deal with consecration.

The Consecrated Worlds Worship modifier is now applied via a dynamic multiplier and can now scale infinitely instead of capping out at a total of twelve "levels" of Consecrated Worlds Worship.

## Compatibility

Overwriting effects and planetary decisions a well as preempting events result in the game logging error messages when first launching.  Expect to see five lines in error.log similar to these:

```
[15:48:05][game_singleobjectdatabase.h:147]: Object with key: recalculate_consecrated_world_modifier already exists
[15:48:05][eventmanager.cpp:355]: an event with id [mega.110] already exists!  file: events/megacorp_events.txt line: 12
[15:48:05][eventmanager.cpp:355]: an event with id [mega.100] already exists!  file: events/megacorp_events.txt line: 73
[15:48:06][game_singleobjectdatabase.h:147]: Object with key: decision_consecrated_worlds already exists
[15:48:06][game_singleobjectdatabase.h:147]: Object with key: decision_unconsecrated_worlds already exists
```

## Changelog

* 1.0.0 Initial version

## Source Code

Hosted on [GitHub](https://github.com/corsairmarks/uncapped_consecration)

### Development Notes

It is best to clone this repository into `<Stellaris User's Directory>/Paradox Interactive/Stellaris/mod`, and then make a connection to the `mod` folder via a `*.mod` file's `path` property.  That will ensure the game can see the files, and also that CWTools will parse them.  Also note that the README.md file exists in the `mod` directory but is symbolically linked in the root directory.