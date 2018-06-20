DFHack 0.44.10-r1
=================

New Scripts
-----------
- `bodyswap`: shifts player control over to another unit in adventure mode
- `devel/find-primitive`: finds a primitive variable in memory
- `gui/autogems`: a configuration UI for the `autogems` plugin

New Tweaks
----------
- `tweak` kitchen-prefs-all: adds an option to toggle cook/brew for all visible items in kitchen preferences
- `tweak` stone-status-all: adds an option to toggle the economic status of all stones

Fixes
-----
- Lua: registered ``dfhack.constructions.designateRemove()`` correctly
- Units::getAnyUnit(): fixed a couple problematic conditions and potential segfaults if global addresses are missing
- `exterminate`: fixed documentation of ``this`` option
- `full-heal`:

    - units no longer have a tendency to melt after being healed
    - healed units are no longer treated as patients by hospital staff
    - healed units no longer attempt to clean themselves unsuccessfully
    - wounded fliers now regain the ability to fly upon being healing
    - now heals suffocation, numbness, infection, spilled guts and gelding

- `liquids`: fixed "range" command to default to 1 for dimensions consistently
- `modtools/create-unit`:

    - creatures of the appropriate age are now spawned as babies or children where applicable
    - fix: civ_id is now properly assigned to historical_figure, resolving several hostility issues (spawned pets are no longer attacked by fortress military!)
    - fix: unnamed creatures are no longer spawned with a string of numbers as a first name

- `prospector`: fixed crash due to invalid vein materials
- `search-plugin`: fixed 4/6 keys in unit screen search
- `stockpiles`: stopped sidebar option from overlapping with `autodump`
- `tweak` block-labors: fixed two causes of crashes related in the v-p-l menu
- `tweak` max-wheelbarrow: fixed conflict with building renaming
- `view-item-info`:

    - fixed an error with some armor
    - stopped appending extra newlines permanently to descriptions


Misc Improvements
-----------------
- Added logo to documentation
- Documented several missing ``dfhack.gui`` Lua functions
- `adv-rumors`: bound to Ctrl-A
- `autogems`: can now blacklist arbitrary gem types (see `gui/autogems`)
- `blueprint`: added a basic Lua API
- `command-prompt`: added support for ``Gui::getSelectedPlant()``
- `devel/export-dt-ini`: added tool offsets for DT 40
- `devel/save-version`: added current DF version to output
- `exterminate`: added more words for current unit, removed warning
- `fpause`: now pauses worldgen as well
- `gui/advfort`: bound to Ctrl-T
- `gui/room-list`: added support for ``Gui::getSelectedBuilding()``
- `gui/unit-info-viewer`: bound to Alt-I
- `install-info`: added information on tweaks
- `modtools/create-unit`: made functions available to other scripts
- `search-plugin`:

    - added support for stone restrictions screen (under ``z``: Status)
    - added support for kitchen preferences (also under ``z``)


API
---
- New functions (all available to Lua as well):

    - ``Buildings::getRoomDescription()``
    - ``Items::checkMandates()``
    - ``Items::canTrade()``
    - ``Items::canTradeWithContents()``
    - ``Items::isRouteVehicle()``
    - ``Items::isSquadEquipment()``
    - ``Kitchen::addExclusion()``
    - ``Kitchen::findExclusion()``
    - ``Kitchen::removeExclusion()``

- syndrome-util: added ``eraseSyndromeData()``

Internals
---------
- Added function names to DFHack's NullPointer and InvalidArgument exceptions
- Added some build scripts for Sublime Text
- Added ``Gui::inRenameBuilding()``
- Changed submodule URLs to relative URLs so that they can be cloned consistently over different protocols (e.g. SSH)
- Fixed compiler warnings on all supported build configurations
- Linux: required plugins to have symbols resolved at link time, for consistency with other platforms
- Windows build scripts now work with non-C system drives

Structures
----------
- ``dfhack_room_quality_level``: new enum
- ``glowing_barrier``: identified ``triggered``, added comments
- ``item_flags2``: renamed ``has_written_content`` to ``unk_book``
- ``kitchen_exc_type``: new enum (for ``ui.kitchen``)
- ``mandate.mode``: now an enum
- ``unit_personality.emotions.flags.memory``: identified
- ``viewscreen_kitchenprefst.forbidden``, ``possible``: now a bitfield, ``kitchen_pref_flag``
- ``world_data.feature_map``: added extensive documentation (in XML)


DFHack 0.44.09-r1
=================

Fixes
-----
- Fixed some CMake warnings (CMP0022)
- Support for building on Ubuntu 18.04
- `digtype`: stopped designating non-vein tiles (open space, trees, etc.)
- `embark-assistant`: fixed detection of reanimating biomes
- `fix/dead-units`: fixed a bug that could remove some arriving (not dead) units
- `labormanager`: fixed crash due to dig jobs targeting some unrevealed map blocks
- `modtools/item-trigger`: fixed token format in help text

Misc Improvements
-----------------
- Reorganized changelogs and improved changelog editing process
- `embark-assistant`:

    - Added search for adamantine
    - Now supports saving/loading profiles

- `fillneeds`: added ``-all`` option to apply to all units
- `modtools/item-trigger`:

    - added the ability to specify inventory mode(s) to trigger on
    - added support for multiple type/material/contaminant conditions

- `remotefortressreader`: added flows, instruments, tool names, campfires, ocean waves, spiderwebs

Internals
---------
- OS X: Can now build with GCC 7 (or older)

Structures
----------
- Several new names in instrument raw structures
- ``army``: added vector new in 0.44.07
- ``building_type``: added human-readable ``name`` attribute
- ``furnace_type``: added human-readable ``name`` attribute
- ``identity``: identified ``profession``, ``civ``
- ``manager_order_template``: fixed last field type
- ``site_reputation_report``: named ``reports`` vector
- ``viewscreen_createquotast``: fixed layout
- ``workshop_type``: added human-readable ``name`` attribute
- ``world.language``: moved ``colors``, ``shapes``, ``patterns`` to ``world.descriptors``
- ``world.reactions``, ``world.reaction_categories``: moved to new compound, ``world.reactions``. Requires renaming:

    - ``world.reactions`` to ``world.reactions.reactions``
    - ``world.reaction_categories`` to ``world.reactions.reaction_categories``



DFHack 0.44.05-r2
=================

New Plugins
-----------
- `embark-assistant`: adds more information and features to embark screen

New Scripts
-----------
- `adv-fix-sleepers`: fixes units in adventure mode who refuse to wake up (:bug:`6798`)
- `hermit`: blocks caravans, migrants, diplomats (for hermit challenge)

New Features
------------
- With ``PRINT_MODE:TEXT``, setting the ``DFHACK_HEADLESS`` environment variable will hide DF's display and allow the console to be used normally. (Note that this is intended for testing and is not very useful for actual gameplay.)

Fixes
-----
- `devel/export-dt-ini`: fix language_name offsets for DT 39.2+
- `devel/inject-raws`: fixed gloves and shoes (old typo causing errors)
- `remotefortressreader`: fixed an issue with not all engravings being included
- `view-item-info`: fixed an error with some shields

Misc Improvements
-----------------
- `adv-rumors`: added more keywords, including names
- `autochop`: can now exclude trees that produce fruit, food, or cookable items
- `remotefortressreader`: added plant type support


DFHack 0.44.05-r1
=================

New Scripts
-----------
- `break-dance`: Breaks up a stuck dance activity
- `devel/check-other-ids`: Checks the validity of "other" vectors in the ``world`` global
- `devel/dump-offsets`: prints an XML version of the global table included in in DF
- `fillneeds`: Use with a unit selected to make them focused and unstressed
- `firestarter`: Lights things on fire: items, locations, entire inventories even!
- `flashstep`: Teleports adventurer to cursor
- `ghostly`: Turns an adventurer into a ghost or back
- `gui/cp437-table`: An in-game CP437 table
- `questport`: Sends your adventurer to the location of your quest log cursor
- `view-unit-reports`: opens the reports screen with combat reports for the selected unit

Fixes
-----
- Fixed a crash that could occur if a symbol table in symbols.xml had no content
- Fixed issues with the console output color affecting the prompt on Windows
- `autolabor`, `autohauler`, `labormanager`: added support for "put item on display" jobs and building/destroying display furniture
- `createitem`: stopped items from teleporting away in some forts
- `devel/inject-raws`:

    - now recognizes spaces in reaction names
    - now recognizes spaces in reaction names

- `dig`: added support for designation priorities - fixes issues with designations from ``digv`` and related commands having extremely high priority
- `dwarfmonitor`:

    - fixed display of creatures and poetic/music/dance forms on ``prefs`` screen
    - added "view unit" option
    - now exposes the selected unit to other tools

- `exportlegends`: fixed an error that could occur when exporting empty lists
- `gui/gm-editor`: fixed an error when editing primitives in Lua tables
- `gui/gm-unit`: can now edit mining skill
- `gui/quickcmd`: stopped error from adding too many commands
- `modtools/create-unit`: fixed error when domesticating units
- `names`: fixed many errors
- `quicksave`: fixed an issue where the "Saving..." indicator often wouldn't appear

Misc Improvements
-----------------
- The console now provides suggestions for built-in commands
- `binpatch`: now reports errors for empty patch files
- `devel/export-dt-ini`: avoid hardcoding flags
- `exportlegends`:

    - reordered some tags to match DF's order
    - added progress indicators for exporting long lists

- `force`: now provides useful help
- `full-heal`:

    - can now select corpses to resurrect
    - now resets body part temperatures upon resurrection to prevent creatures from freezing/melting again
    - now resets units' vanish countdown to reverse effects of `exterminate`

- `gui/gm-editor`: added enum names to enum edit dialogs
- `gui/gm-unit`:

    - made skill search case-insensitive
    - added a profession editor
    - misc. layout improvements

- `gui/liquids`: added more keybindings: 0-7 to change liquid level, P/B to cycle backwards
- `gui/pathable`: added tile types to sidebar
- `gui/rename`: added "clear" and "special characters" options
- `launch`: can now ride creatures
- `modtools/skill-change`:

    - now updates skill levels appropriately
    - only prints output if ``-loud`` is passed

- `names`: can now edit names of units
- `remotefortressreader`:

    - includes item stack sizes
    - some performance improvements
    - support for moving adventurers
    - support for vehicles, gem shapes, item volume, art images, item improvements


Removed
-------
- `tweak`: ``kitchen-keys``: :bug:`614` fixed in DF 0.44.04
- `warn-stuck-trees`: :bug:`9252` fixed in DF 0.44.01

Internals
---------
- ``Gui::getAnyUnit()`` supports many more screens/menus

Structures
----------
- Added ``buildings_other_id.DISPLAY_CASE``
- Added ``job_type.PutItemOnDisplay``
- Added ``twbt_render_map`` code offset on x64
- Fixed an issue preventing ``enabler`` from being allocated by DFHack
- Fixed ``unit`` alignment
- Fixed ``viewscreen_titlest.start_savegames`` alignment
- Found ``renderer`` vtable on osx64
- Identified ``historical_entity.unknown1b.deities`` (deity IDs)
- Located ``start_dwarf_count`` offset for all builds except 64-bit Linux; `startdwarf` should work now
- New globals:

    - ``version``
    - ``min_load_version``
    - ``movie_version``
    - ``basic_seed``
    - ``title``
    - ``title_spaced``
    - ``ui_building_resize_radius``
    - ``soul_next_id``

- The former ``announcements`` global is now a field in ``d_init``
- The ``ui_menu_width`` global is now a 2-byte array; the second item is the former ``ui_area_map_width`` global, which is now removed
- ``adventure_movement_optionst``, ``adventure_movement_hold_tilest``, ``adventure_movement_climbst``: named coordinate fields
- ``artifact_record``: fixed layout (changed in 0.44.04)
- ``incident``: fixed layout (changed in 0.44.01) - note that many fields have moved
- ``mission``: added type
- ``unit``: added 3 new vmethods: ``getCreatureTile``, ``getCorpseTile``, ``getGlowTile``
- ``viewscreen_assign_display_itemst``: fixed layout on x64 and identified many fields
- ``viewscreen_reportlistst``: fixed layout, added ``mission_id`` vector
- ``world.status``: named ``missions`` vector
- ``world`` fields formerly beginning with ``job_`` are now fields of ``world.jobs``, e.g. ``world.job_list`` is now ``world.jobs.list``

Lua
---
- Added a new ``dfhack.console`` API
- API can now wrap functions with 12 or 13 parameters
- Exposed ``get_vector()`` (from C++) for all types that support ``find()``, e.g. ``df.unit.get_vector() == df.global.world.units.all``
- Improved ``json`` I/O error messages
- Stopped a crash when trying to create instances of classes whose vtable addresses are not available


