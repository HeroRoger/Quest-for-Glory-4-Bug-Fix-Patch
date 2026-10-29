# QFG4 Fix Pack for Enhanced 1.2 - version 1.0

## How it was tested
**Every fix was checked by automated tests. For almost every fix, these tests run the game's own scripts with the fix in place; the rest (a few copies of ScummVM's own fixes and tiny edits) were checked byte by byte. Many fixes were also tried in DOSBox and ScummVM. The whole game has not been played start to finish with this patch, so keep backups of your game and your saves.**

---

## 1. What this patch is

- A bug-fix patch for **Quest for Glory IV: Shadows of Darkness**, the **CD version** in **English** (the GOG and Steam copies are the CD version).
- It is built **on top of "QFG4 Enhanced 1.2"** (AshLancer's Enhanced Update, continued by DoomLazer). **You need Enhanced 1.2 installed first.** This patch does not work on its own.
- It fixes crashes, lockups, seven dead ends, a likely cause of "save rot", and timing problems that make the game misbehave on fast computers. It also brings over many of ScummVM's built-in fixes, so DOSBox players get them too.
- It changes no art, music, voices or story. Rooms, puzzles and dialogue are Sierra's (and Enhanced's).
- Every fix was made the careful way. The game's existing code is never moved; fixes either swap a few bytes in place or add a small piece of code at the end of a file. This is also why DOS saved games keep working (ScummVM needs a new game; see section 5).

## 2. Installing

**Before you start:** make a backup copy of your whole Quest for Glory IV folder (or at least its `PATCHES` folder). Then you can always go back.

**Step 1: Install QFG4 Enhanced 1.2 (skip this if you already have it).**
- Enhanced 1.2 comes as a zip (`QFG4.Enhanced.1.2.zip`). Inside are a `PATCHES` folder and two text files.
- First move the game's old `PATCHES` folder out of the way, as Enhanced 1.2's own readme says: rename it, for example to `PATCHES_BAK` (skip this if there is no `PATCHES` folder). Some copies, such as GOG's, come with older fan fixes that Enhanced 1.2 replaces. Then extract the zip into your QFG4 game folder, so that its `PATCHES` folder ends up in the game folder. Say yes if asked to overwrite.
- Typical game folders (from the Enhanced readme):
  - `C:\Sierra\Quest for Glory Collection Series\Quest for Glory 4`
  - `C:\Program Files (x86)\GOG Galaxy\Games\Quest for Glory Series\Quest for Glory 4`
  - `C:\Program Files (x86)\Steam\SteamApps\Common\Quest For Glory Collection\QFG4`
- The game folder is the one that contains `RESOURCE.MAP` and `RESOURCE.000`.
- **Check:** after extracting, the `.scr` and `.hep` files must sit directly inside `PATCHES`. If you see a `PATCHES` folder inside `PATCHES`, move its files up one level.

**Step 2: Install this patch.**
- Extract this patch's `PATCHES` folder into the same game folder, so its files land in the same `PATCHES` folder as Enhanced 1.2's files. Say **yes** when asked to overwrite.
  - 24 of Enhanced's files are replaced by fixed versions: `7`, `13`, `26`, `53`, `89`, `250`, `270`, `290`, `300`, `320`, `360`, `500`, `510`, `580`, `600`, `625`, `630`, `640`, `650`, `710`, `730`, `750`, `770`, `810` (the `.scr` files only).
  - **Keep all of Enhanced's `.hep` files.** They are still needed.
- If your copy keeps its patch files directly in the game folder instead of a `PATCHES` folder, put this patch's files wherever Enhanced 1.2's files are. The rule: **one copy of each file, in the same place as Enhanced 1.2's files.** Do not leave two different copies of the same number in two folders.
- **Not sure which folder the game reads?** Open `RESOURCE.CFG` in the game folder with Notepad and find the `patchDir` line. It lists the folders where the game looks for patch files. A copy installed from the original CD with Sierra's installer usually lists only the game folder itself (plus the CD), with no `PATCHES` folder. In that case, put both Enhanced 1.2's files and this patch's files directly into the game folder. (ScummVM should find the files in either place; see section 4.)
- **GOG copies, and any copy with older fan fixes:** Enhanced 1.2 has only three `.hep` files: `53`, `710` and `730`. Look in the `PATCHES` folder and in the game folder itself for any other `.hep` file whose number matches one of this patch's `.scr` files (for example `803.hep`). If you find one, move it into your backup. It belongs to an older fan fix (such as NewRisingSun's, which GOG copies include) that this patch replaces, and mixing it with this patch's `.scr` file of the same number can crash the game (for `803`: on the slippery slope at the Standing Squid Stone). Any other `.hep` file can stay.
- **Linux / macOS:** the file names must match exactly, including upper and lower case. If you now see two files whose names differ only in case (for example `803.scr` and `803.SCR`), keep this patch's lowercase file and move the other one into your backup.

**Step 3: Play.** Load your saved game or start a new one (see section 5).

**To uninstall:** put back your backup `PATCHES` folder, or delete this patch's files and extract Enhanced 1.2 again (overwrite when asked).

## 3. DOSBox notes

- **Recommended setting: `cycles=max`** (in the `[cpu]` section of your DOSBox settings file; GOG and Steam copies come with their own `.conf` file). Our own DOSBox tests (DOSBox Staging) ran at `max`; in DOSBox Staging, set `cpu_cycles = max` and `cpu_cycles_protected = auto`.
  - This patch limits the game to at most 60 frames per second (the same speed as ScummVM), and combat to 20. So a fast DOSBox setting no longer makes spell effects, the Vorpal Bunny, the barrows wraith or combat run too fast.
  - If the sound stutters at `max`, try a fixed number instead, for example `cycles=fixed 30000`, and adjust from there.
- **You no longer need to slow DOSBox down** to make combat playable (old advice for this game). Very low settings make the game behave like a slow 1993 PC. That has its own small timing problems, so avoid going very low.
- What combat should feel like now, at any setting:
  - the power bar fills in under a second;
  - thrown daggers and spells cross the screen in about one and a half seconds.
- The game's own **Speed** slider (in Options) only changes how fast your hero walks and animates. Any position is fine.
- **Old saves:** after loading a save made before you installed this patch, drag the Speed slider once (even back to the same spot). Only a drag stores your choice, and the game returns to the stored speed after many scenes (for example after climbing the rope into the final chamber).

## 4. ScummVM notes

- This patch works with ScummVM too. Add the game folder in ScummVM as usual; it also reads the `PATCHES` folder. You do not need to change any ScummVM setting.
- **ScummVM's own fixes step aside automatically.**
  - ScummVM repairs many QFG4 bugs while the game runs. It recognises each buggy spot by its exact bytes.
  - Where this patch fixes the same spot, it either uses ScummVM's own fix byte for byte, or replaces that spot so completely that ScummVM no longer recognises it. Either way the fix is applied once, never twice, and never half.
  - We checked every one of ScummVM's QFG4 fixes against this patch: no conflicts.
- **What ScummVM players gain:**
  - Enhanced 1.2 rebuilt some scripts, so ScummVM could no longer recognise them and some of its fixes silently stopped working. This patch brings those back:
    - the capture chase repeating;
    - the Burgomeister's empty office;
    - the Open spell's effect;
    - a thrown weapon killing Ad Avis;
    - the fighter's endless staff animation;
    - the town gate message at night;
    - the bone cage;
    - the moon showing on the time panel by day;
    - the innkeeper's talk topics at night, when he is away;
    - the lock squeak in the castle room with three doors.
  - In combat, thrown daggers and spells no longer crawl slowly across the screen in ScummVM (ScummVM ticket #17017).
  - The fixes that are ours alone also apply (for example the endgame clock, the barrows wraith, and the west street when you rest).
- The 60-frames-per-second limit changes nothing in ScummVM, which already runs at that speed.

## 5. Saved games

- **DOS (the original interpreter, for example in DOSBox): saved games made with Enhanced 1.2 keep working with this patch.**
  - This patch never changes the parts of the game that DOS saved games store (the `.hep` files).
  - Your current game can carry on with the fixes in place.
- **ScummVM: start a new game after installing this patch.** ScummVM saves made with plain Enhanced 1.2 will not load (ScummVM stops with an error).
  - A ScummVM save remembers where things sit inside each game script that was in memory. Many of these fixes add code to scripts, which moves those places, so an older save no longer fits.
  - Saves you make after installing the patch work as usual.
- **Saves from before you installed Enhanced 1.2 still will not work.** Enhanced 1.2 itself needs a new game (see its readme). This patch does not change that.
- If you saved while already stuck (hero frozen, controls locked), loading that save may not unstick you. Load an earlier save from before the problem.
- **"Save rot"** (saves that get slower and slower until screens crash):
  - this patch removes what we believe is the main cause, a small memory leak in the autosave;
  - it cannot clean a save that has already rotted;
  - keeping several saves per play-through is still a good idea.
- If you uninstall this patch, saves made with it should still load under plain Enhanced 1.2 in DOS. *(Not yet tested.)* In ScummVM they will not, for the same reason as above.

## 6. What is fixed

*Spoiler warning: some lines mention late-game events.* Names in [brackets] help us if you report a problem.

### Crashes (the game stops with an error)
1. Using the inn door in the west street from some spots no longer crashes the game. [motion-crashes-260-803]
2. Walking up, walking down and sliding down the slippery slope at the Standing Squid Stone no longer crash the game (3 different spots). [motion-crashes-260-803]
3. Pressing the arrow keys on the character sheet no longer crashes the game. [keyboard-crashes-15-26]
4. Pressing the arrow keys or Tab on the death screen no longer crashes the game. [keyboard-crashes-15-26]
5. The necrotaurs capturing you in the forest no longer crash the game (two different crashes). The scene's pause is now a steady 4 seconds instead of depending on PC speed. [necrotaur-capture-51]
6. Hitting the rock pile at the Squid Stone before your hero has finished the throwing motion no longer crashes the game. [rockpile-800]
7. Casting Trigger or Levitate after using the grapnel at the Squid Stone no longer crashes the game. [grapnel-800]
8. Jumping from a hummock to the shore in the swamp when it is too far no longer crashes the game ("Not an Object"). [swamp-shore-530]
9. Clicking the very corner of a screen next to a side with no exit (for example the top-right corner of some forest screens) no longer walks the hero off that side into an error. [edge-exit-17]
10. After you used Fetch at the Standing Squid Stone, or knocked its rocks down, a later Fetch (for example on the mana fruit tree or the Dark One's archway) no longer risks a "Not an Object" crash in DOSBox. This is a bug on Sierra's own 1994 list. [fetch-list-37]
11. In the blood cave, freezing a flow of blood with Frostbite and then pushing the rock no longer crashes the game when the flow would have thawed (Sierra's 1994 bug #9). [frost-push-740]
12. In the faerie fight, killing a faerie while she is casting or giving the "use your area attacks" hint no longer crashes the game. [faerie-hint-580]
13. Walking away from the rusalka while she is talking (or from the Leshy's bush while its giggle text is up, from Bella's table at the inn during her thank-you lines, or from the lab while the antwerp catch line is up) no longer risks a "Not an Object" crash in DOSBox. [room-cues-5]
14. Failing to pick the lock of the gnome's door at the inn no longer shows a "message not found" box and crashes. [gnome-door-320]
15. Opening the character sheet and moving the mouse over it no longer risks "Error 47: Not an Object" (seen after restoring a save). [charsheet-temp5-15]
16. Double-clicking the practice safe in the Thieves' Guild no longer crashes the game. [safe-click-89]
17. Walking off the Elderbury bush screen while its "That hurt. That REALLY hurt..." line is still up (after the bush clawed you) no longer risks a "Not an Object" crash in DOSBox. [claw-line-570]
18. Leaving the monastery by Levitate (floating up through the window, or fleeing the monks) no longer crashes the game as you land outside. This was a slip in Enhanced 1.2. [levitate-exit-250]
19. If Igor has already died, opening his grave with the rope after climbing the oak no longer crashes the game when the scene ends. [tree-rope-500]
20. Telling the Leshy the "bush in goo" answer to its riddle no longer looks up a missing message right after the points. Older ScummVM versions stopped with an error there (current ScummVM works around it; DOS was not affected). [leshy-goo-579]
21. In the forest, if you killed a monster with spells or thrown daggers before it reached you, casting Calm on the same screen no longer crashes the game ("Not an Object"); you now get the normal "A feeling of peace and tranquility permeates the area." Casting Calm or Dazzle while such a monster is still falling over no longer crashes the game either; Calm gives its normal reply there and Dazzle has no effect. [forest-calm-50]
22. In the Burgomeister's office, a Paladin telling about Piotyr's sword while the Burgomeister is not there (climbing in through the window in the early evening, with Gypsy Davy in the cell) no longer crashes the game ("Not an Object") right after the line, or when you leave the office afterwards; you get the magic shield as usual. Probably bug #17 on Sierra's 1994 list. [burgo-shield-300]
23. In the swamp, casting Fetch no longer crashes the game ("Not an Object") after the Will-o'-Wisps are gone: after you caught them and stayed on that shore screen until dawn (the flask expires), or after you released them deeper in the swamp and they flew off. Catching live wisps with Fetch at night works as before. [wisp-fetch-10]
24. In the cave room with the altar, casting Dazzle while the Sense Ritual's sparks are flashing no longer crashes the game ("Not an Object"). This could only happen at fast Speed slider settings, when the spell ended before the lit spark finished. [spark-cue-760]
25. In automatic ("strategy") fights, a hero with magic who knows none of Force Bolt, Lightning Ball and Frost Bite no longer "casts" a leftover spell over and over, each time doing more damage, until the game crashes with Error 49. The hero now casts Flame Dart in that case, as the automatic fight already does by default. [auto-spell-41]
26. In the endgame pit cave, after you had crossed the pit once, holding up the sheet as a sail on the start side and then doing anything but casting Levitate no longer stops the game with an error ("Not an object"). You now just put the sheet away, as on the first try. This bug came with Enhanced 1.2. [sail-abort-710]

### Lockups (the game keeps running, but you cannot do anything)
1. Casting Trigger after a successful Summon Staff now gives you control back. [trigger-11]
2. Throwing when you have exactly two daggers no longer locks the game, and every throw now uses up exactly one dagger or rock, not two or three. This applies at the castle gate, against the ghost in the castle, against Ad Avis, and in the Blood Ritual room. [projectile-use-600-625-730-740]
3. A thief choosing Open on either door in the castle room with two doors ("The door won't budge") no longer leaves the controls locked. [rogue-door-644]
4. In the bone cage, both choices (Break Cage and Jump Out) now play the whole scene before you get control back. Before, one click during the escape could freeze the game for good. [bone-cage-770]
5. In the final battle at a slow Speed setting, the hero's spell no longer gives you control in the middle of Ad Avis's death scene, where a click could stop the scene for good. [adavis-death-730]
6. Using food on the Elderbury bush while standing on the path at the top of its screen no longer freezes the game; the thrown rock used to hang in the air. [bush-throw-570]
7. In the blood cave, casting Flame Dart at a flow of blood no longer freezes the hero. [blood-freeze-740]
8. After winning the faerie fight, throwing or casting in the clearing no longer freezes the hero. [faerie-freeze-580]
9. In the faerie ring, casting Calm or Summon Staff after taking the illusory staff no longer freezes the hero. [staff-cue-580]
10. At Igor's grave, casting Open on the already-open grave no longer freezes the hero. [open-grave-500]
11. While chained in the castle dungeon, casting Open on the Iron Maiden no longer freezes the hero. [maiden-open-670]
12. Choosing "pick the lock" on the boarded-up Adventurers' Guild door by day, or failing it at night, no longer leaves the controls locked. [guild-lock-250]
13. In the castle stairways, a Thief failing to pick the lower door's lock from the door menu no longer loses control. [castle-lock-633]
14. After Tanya is restored, throwing a dagger or rock or casting an attack spell in her empty room no longer locks the controls (the scene waited for a girl who is no longer there). [tanya-guard-650]
15. In the Breath Altar cave, a Magic User held at the hole by the wind who casts any spell except Calm or Open no longer freezes there for good: the wind goes on, and Calm then Open still free you. [wind-spell-750]
16. At the castle gate, if you had killed the Necrotaurs and came back out of the castle after midnight, casting Levitate there no longer freezes the game: the hero used to land, turn as if a Necrotaur grabbed him, and wait for a Necrotaur that was not there. [necro-levitate-600]
17. Outside the town gate, after Tanya is rescued, a Wizard casting Ritual of Release on the ground at night no longer freezes the game (the staff scene waited for a staff that is no longer there); he now gets the same "shouldn't use magic" reply as by day. [ritual-release-270]
18. At the Squid Stone, after the rock pile has collapsed, throwing one more dagger at the pile or the goo no longer freezes the game: the dagger used to hit and nothing came back. You now get "You missed.", as with a thrown rock. [pile-dagger-800]
19. On the monastery street, if you arrived at night and stayed (or rested) until after 5:00 AM, using your hand, lockpick or toolkit on the monastery door no longer freezes the game: Igor's "go away" scene used to start for an Igor who was not there. Now the door just works as it does when Igor is gone; when Igor is really standing there, nothing changes. [igor-dawn-250]
20. In Baba Yaga's hut on your first visit, while you are trapped in the ice, telling her about the Gnome several times (with other topics in between) no longer freezes the hero in the ice for good: her scene used to run past its last step. Every Gnome pick now leads to the same "Eye Pie" scene as the first one, and you end up outside the hut as usual. [gnome-tell-490]
21. In fights, a Thief who kills the monster with a thrown dagger no longer gets stuck with the controls locked: the dead monster used to keep fighting until it hit the hero, and the Pit Horror in the Dark One's cave, which never moves, could fail to ever reach the hero, so the fight never ended. A dagger kill now ends the fight at once, as a sword kill does. [dagger-kill-810]
22. In Erana's garden (the Wizard's tulip puzzle), casting Open on the tulip just before it closes no longer leaves you with no controls for good. This needed a slow PC or very low DOSBox cycles (or a pause at that moment): the tulip closed while it was still opening. Opening the tulip now restarts its timer, as casting Fetch on it already did, so it stays open for a while; left alone it still closes after 20 seconds. [tulip-timer-440]
23. Erana's dreams (the kiss dream and a later one) no longer freeze the game for good on fast computers at the slow dissolve right after her face appears. Her picture now appears at once instead of dissolving in. [dream-cut-110]
24. Very rarely, at random (about once in 65,536 lines, and a whole game has thousands), a message box or a talking portrait used to stay on screen forever and ignore every click and key, so you had to quit. Every line now ends as it should. This is ScummVM's own fix, so DOSBox players get it too. [narrator-lockup-59-64928]

### Dead ends (you can no longer finish the game)
1. **The Domovoi:** if Bella woke you at the inn before you talked to the Domovoi, talking to him no longer counted, so you could never get the doll. This could still happen with Enhanced 1.2 and is now fixed. [domovoi-324]
2. **Igor and the gypsy:** on day 5 the townsfolk gather outside the inn because Igor is missing and the gypsy has been jailed. This only happened if you had talked to the Burgomeister twice before. If the monastery had burned, or Nikolai had left, before your second talk with him at his window, that talk never came, so the Igor story never started and the gypsy camp stayed closed for good (unless you happened to visit his office). The scene now starts on day 5 either way. [igor-plot-260]
3. **The monastery fire:** a Flame Dart on the curtain or rug could burn the monastery before you rehydrated the Domovoi statue inside, and you could then never get Tanya's doll. Now the spell waits for the same steps as the torch. [monastery-fire-360]
4. **The Wizard's staff in the final battle:** if a Wizard summoned the magic staff and then threw a rock or dagger at Ad Avis, the staff left his hands, but Summon Staff kept saying "You've already summoned the staff". Only spells cast with the staff can kill Ad Avis, so the battle could no longer be won. You can now summon the staff again, as on the original CD. [staff-resummon-730]
5. **No dagger in the endgame:** in the endgame you must open a stone valve with a dagger to leave the Bone Ritual cave. If you had thrown your last dagger earlier (at the badders on the castle stairs, or at the faeries when they trap you), you were stuck there for good. Now the skeleton in that cave gives you a dagger again, but only if you have none. [last-dagger-770]
6. **The castle great hall (Thief):** entering the great hall from the barrel room used to put you inside the closed door's area, so you walked straight back out, every time, and the side rooms have no other way on. Now you arrive in the hall. [great-hall-630]
7. **A Thief chained in the castle:** a Thief carried off to the castle and chained there could only get free with the Thieves' Toolkit, so without it the game could not go on. Now the plain lockpick works too, and a Thief with lock-picking skill can open the chains with Do. [thief-chains-670]

### Other fixes

**Saved games and memory**
1. Each autosave left a small piece of unused data in memory, which was then stored in every later save (checked in DOSBox: one piece per autosave in the original game, none with this fix). This is our best guess at the cause of "save rot", but it is not proven. [autosave-leak-0]
2. Casting Trigger no longer leaves unused data in memory with every cast. [trigger-11]
3. Casting Summon Staff no longer leaves unused data in memory with every cast. [staff-leak-46]
4. After Restart, inventory items no longer keep their old state (for example, the torch already showing as lit). [restart-leaks-0]
5. Restoring a saved game no longer leaves unused data in memory each time: three small pieces of text, the restore list's copy of the save name you picked, an extra copy of the restore list itself, the room's timers, the clock's sleep/time panel when it was loaded, the spell scripts of Trigger, Detect Magic, Dazzle, Calm and Summon Staff after a cast, and, when you restore from the death screen, the whole death screen (DOSBox; the original game kept them and stored them in every later save). [restore-leak-64994]
6. Each save also stored the save routine's own work data, which came back with every restore and was stored again with the next save, so it piled up the more you saved and restored (6 pieces every time the autosave was restored, for example after dying). It is now freed right after each restore. [save-orphans-0-64994]
7. Releasing the Will-o'-Wisps after catching them on the same swamp screen no longer leaves the old wisp list in memory (checked in DOSBox: the original game kept one per release and stored it in every later save). [wisp-leak-10]
8. Message boxes with a plain line of text, such as the box asking which save to replace when all 20 save slots are full and some error boxes, no longer leave a small piece of unused data in memory each time (checked in DOSBox: the original game kept one per box and stored it in every later save; most game messages never had this problem). In ScummVM you will see no difference. [print-leak-64921]
9. The save/restore list no longer leaves two small pieces of unused data in memory each time it is refreshed, which happens after every Change Directory you accept and every save you delete (checked in DOSBox: the original game kept them and stored them in every later save). In ScummVM you will see no difference. [srdialog-leak-64990]
10. The Automatic Save is no longer made when the hero is already doomed, so loading it no longer kills him again. This happened after losing to the Pit Horror in the castle, after losing a forest fight on the Elderbury bush screen, and when coming back to Tanya's door at night after attacking Toby. [doomed-autosave-570-650-710]

**Speed and timing** (mostly for DOSBox on fast settings)
1. The game now runs at most 60 frames per second, the same as ScummVM (everywhere except Cranium's door puzzle, which keeps its own pace). Spell effects, the Vorpal Bunny, the cave badgers and zoom close-ups no longer race on fast settings. [frame-cap-0]
2. Combat now runs at a steady speed on any computer, and thrown daggers and spells fly at a fixed speed. Before, they depended on a speed test the game runs at startup, which made them crawl in ScummVM. [combat-speed-34-38]
3. At the barrows, before the fight, the wraith now drains about 2 health per second on every computer (the rate of a typical 1993 PC). Before, it was about 10 in ScummVM and could kill you almost instantly in DOSBox on fast settings. [wraith-drain-53]
4. In the endgame caves and at the reward ceremony, talking to someone no longer restarts the game clock. Before, hunger, poison and spell timers ran during the finale. [cave-clock-59]
5. The same for casting Juggling Lights in the endgame caves: it no longer restarts the game clock. [juggle-clock-62]
6. After a forest fight, the space you have to walk around the monster's body now matches the body lying on the ground at any speed. [corpse-size-50]
7. Casting Juggling Lights in the Borgov crypt no longer stops the game clock. Before, the time of day, hunger, healing, Stamina and Mana recovery, poison and spell timers stood still afterwards until you next talked to someone, bought something or dreamed (an Enhanced slip; the spell works in the crypt only since Enhanced). [juggle-clock-510]

**Story and logic**
1. After you have been captured, the necrotaur chase and the dungeon sequence can no longer happen a second time when you walk through the town gate. And if you get away from the night chase into town (over the gate, with the grapnel or by Levitate), leaving town by day no longer brings the necrotaurs and Ad Avis in broad daylight. If your save was made while that unwanted chase had already started, it plays out that one time; the fix works from your next arrival at the town gate. [chase-repeat-290]
2. After the geas, arriving at the castle gate from the dungeon, you can no longer walk through the closed gate, and the gate's menu matches night-time. [geas-gate-600]
3. In the final battle, after Ad Avis's joke, a thrown dagger or rock can no longer kill him; only a spell can, as intended. [adavis-throw-730]
4. On the character-select screen, clicking a door while it is still opening now gives you the class you clicked. This also fixes the Enhanced known issue where the Fighter's door picked the last class you tried. [char-select-140]
5. The runes puzzle at the Squid Stone no longer rejects the right answer when you click the letters quickly. [runes-801]
6. In the castle's iron-safe room, the east door no longer sends you out the west side, and oiling one door no longer marks the other one as oiled. [iron-safe-643]
7. In the castle, picking a lock now checks that door's own oil, so oiling one door no longer silences the squeak of the other doors. [lock-squeaks-634-642-643-644-661]
8. The same fix for the castle room with three doors: picking a lock there now squeaks unless that door is oiled. Before, oiling any one of the three silenced all of them. [lock-squeak-640]
9. The revenant now drops a random amount of kopeks (15 to 40), not always 15. [small-fixes-11-28-31-50-475-800]
10. After you eat your last ration, the rations icon no longer stays selected. [small-fixes-11-28-31-50-475-800]
11. Everywhere in the game, if a thrown weapon or spell hits its target before your hero finishes the throwing motion, the hero is now put back to normal. Before, he was left frozen mid-throw, which could block spells. [throw-interrupt-32]
12. The Vorpal Bunny no longer stops attacking for good when it is pushed to the right edge of the screen (you could still hit it and win; a spell or dagger hit started its attacks again). [bunny-820]
13. Asking Davy about "Hunting" early no longer makes the Leshy skip his 4th meeting (his "Rusalka" question, 2 points, and his parting riddle about Baba Yaga's hut). [leshy-meeting-579]
14. A Paladin who beats the Pit Horror now gets the 4 points, as a Fighter does. [paladin-points-710]
15. Magda the fortune teller now tells a Magic User his visions and gives him the right plant hint (the code asked for a class that does not exist). [magda-class-470]
16. After a Badder pack chases you into the wraith mounds at night, the next monster no longer comes as four at once and follows you for rooms. [barrow-chase-53]
17. The tic-tac-toe trap puzzle (the Thieves' Guild safe, the castle chests, the desk) no longer remembers an old full board, so quitting a later puzzle half-way no longer sets off the trap. [tictac-mark-648]
18. A Paladin whose honor jumps past several levels at once (for example after a big reward) now gets, or loses, each of those honor powers, such as the Honor Shield: one more at each later honor change, with one message each. [paladin-honor-28]

**Text, sound and pictures**
1. In the castle, the door responses and the door squeak by the great hall (the room above the stairs), the great hall keyhole message, and the "peer" message at the lower bat door are now correct. Looking around the dungeon no longer prints two messages. [castle-texts-633-644-663-670]
2. At night, after Katrina and Ad Avis have had their argument, the great hall door no longer offers the argument options again. [door-options-633]
3. In the Burgomeister's office, Talk no longer offers Burgomeister topics when nobody is there. [burgo-teller-300]
4. The Open spell's green effect now appears every time you cast it, not just the first time. [open-effect-13]
5. The Trigger spell's effect now appears every time you cast it, not just the first time. [small-fixes-11-28-31-50-475-800]
6. Levitating at the Squid Stone and in other places no longer shows a stray technical "vanishingY" message. [small-fixes-11-28-31-50-475-800]
7. The fortune teller's tarot readings now show the right cards, in the right places. [small-fixes-11-28-31-50-475-800]
8. At the inn, late in the game, Talk on the hero no longer offers innkeeper topics between 11 pm and 5 am, when he is not in the room. [absent-innkeeper-320]
9. Casting spells in a fight no longer makes the Open spell cost 8 to 12 Mana Points instead of 2. (A saved game made after such a fight keeps the wrong cost until you Restart.) [open-cost-40-41]
10. Punny Bones' joke chair no longer leaves the hero walking at top speed; the hero goes back to the speed you set. [chair-speed-240]
11. The game no longer forgets your Speed setting after two special scenes: the angry faeries at night in the faerie clearing (Magic User) and climbing the rope into the final chamber. Before, the hero went back to normal speed there and you had to move the Speed slider again. Many other scenes (climbing, the graveyard tree, the crypt and more) now also play at your speed. In a saved game from before the patch, move the slider once. [speed-restore-25]
12. In ScummVM, clicking the street that leads up from Erana's staff to Dr. Cranium's and Nikolai's houses takes you there again (an Enhanced slip made that click zone never work in ScummVM). [east-exit-270]
13. In the swamp, ending a Glide on a hummock or back on the shore no longer changes the hero's speed (he used to zoom around at a crazy speed on a first visit, or slow down later). [swamp-speed-10-570]
14. The Will-o'-Wisps can now be caught again after you released them in the swamp. Before, new candy made them stay "almost in reach" until you left that screen, and catching them again too early could crash the game. [wisp-count-10]
15. If Igor died because you did not rescue him in time, he no longer appears alive at the ending ceremony. [igor-ending-635]
16. Castle gate screen: the click strip along the bottom handles its own clicks again, as on the CD (the same Enhanced slip as item 12). You will not see a difference: in our tests the hero already walked off the bottom of the screen before, in DOSBox and ScummVM. [south-exit-600]
17. Quitting the castle chest's trap puzzle (tic-tac-toe) without solving it no longer leaves the cursor stuck as a menu arrow. [chest-trap-643]
18. A failed climb up the cemetery oak no longer changes the hero's walking speed; your Speed setting comes back. [oak-speed-500]
19. The jumps in the lava cave (to the island and up to the shelf) no longer throw away your Speed setting. [lava-speed-740]
20. In a revenant fight while wearing the fortune teller's Amulet, the revenant no longer gains or loses a random amount of health each time it hits you (DOSBox; ScummVM already behaved). [revenant-amulet-830]
21. Importing a hero you exported from QFG4 itself now brings back every skill and spell where it belongs. Before, most spells and HP/SP/MP slid one place (Force Bolt, Detect Magic and others lost or swapped), and Acrobatics plus the QFG4 spells (Frost Bite, Ritual of Release, Hide, Aura, Protection, Resistance, Glide) were lost. A QFG2 hero no longer gets pill counts as spells. A QFG3 or QFG4 Fighter who had learned certain spell pairs (such as Zap and Reversal) no longer turns into a Magic User. [import-fix-54]
22. A hero with a lot of experience (about 11,500 or more) is now exported in a form QFG5 accepts; experience above 9,999 is saved as 9,999. Before, QFG5 said the file was too big or the wrong file. [export-exp-52]
23. The time panel no longer keeps showing the moon by day after you looked at it at night in the same place (for example after sleeping until morning at the inn). [moonrise-7]
24. At the cemetery, when you tie the rope to the oak branch to rescue Igor, the two ropes are no longer drawn behind the crypt pillars until they start moving (DOSBox; ScummVM already showed them right). [graveyard-rope-500]
25. A fighter or paladin taking the staff in the final battle, after having thrown something, no longer keeps animating forever (you already got control back; only the animation never ended). [staff-pose-730]
26. At the town gate at night, the "gate is barred" message and menu no longer come back a second time; your hero now steps clear of the gate. [gate-mat-270]
27. In Speech only mode (Text off), a line with no recorded voice now shows its text for the normal reading time instead of being lost. [speech-fallback-59-64928]
28. Floating out of the monastery by Levitate when the monks catch you no longer loses your Speed setting. [levitate-speed-360]
29. Setting the monastery on fire after climbing in over the wall no longer leaves the hero walking slowly; your Speed setting comes back. [fire-speed-360]

Counted together: 26 crashes, 24 lockups, 7 dead ends, and 64 other fixes (a few of them share a fix name).

## 7. Known issues (not fixed yet)

**Bugs we know about but have not fixed:**
- **Castle gate sword picture:** if you attack the castle gate with any sword, the hero is shown swinging the same sword, whatever sword you actually carry. Enhanced 1.2 already fixed this for the axe. This is cosmetic. (ScummVM ticket #13822.)
  - The other castle gate tickets (Force Bolt "glances off", Flame Dart breaking Summon Staff, Juggling Lights saying "no effect") appear to be fixed already by Enhanced 1.2's rewrite of the castle gate. (Checked in the game's scripts, not yet in play.)
- **Caught at dawn:** if morning comes while you are escaping from the Burgomeister's office, you are still caught, even mid-escape. This was probably intended by the designers.
- **Small cosmetic timing slips:** a few short animations can be cut off, for example:
  - planting the bonsai in the magic garden;
  - Toby's door;
  - an oiled castle door opening.
- **A few rare, very small memory leaks** remain: a message dropped when you leave a room at the exact wrong moment, and two rare error paths.
- **Very slow DOSBox settings** can bring back "slow PC" timing problems that the game had on 1993 computers. See section 3.
- **Ad Avis and spells at very low speed:** Enhanced 1.2 most likely fixed this already, but it has not been confirmed.
- **Importing a QFG3 hero (very rare):** if the hero's experience is exactly one of 18 values between 24,685 and 27,344, the game reads the file as a QFG4 hero, and the hero arrives with 150 experience and a huge Acrobatics value. Plain Enhanced 1.2 reads these heroes right. If it happens, earn a few more experience points in QFG3, export again and import the new file.
- **ScummVM only, cosmetic:** on the tightrope in the endgame cave, the tentacle that grabs the hero may stop moving. Enhanced 1.2 rebuilt that script, so ScummVM's own fix no longer applies, and this patch does not bring it back.

**Not a bug, but easy to miss:**
- **Katrina's note never comes:** after you save Toby at Erana's staff, the note ("Meet me at the castle gates tonight") only appears once you have also heard the gnome's Ultimate Joke (Punny Bones' room at the inn). Learn the joke, then sleep in your room at the inn; the note is on the bed when you wake.

**Known issues listed by Enhanced 1.2 that this patch does not change:**
- The Paladin always has Sense Danger, whatever his Honor.
- Some Paladin abilities (Flaming Sword, Heal, Honor Shield) arrive at the wrong Honor values.
- On the death screen, pressing Restore and Cancel again and again slowly moves the text and picture down the box.
- Some lines are missing their voice, or play the wrong one, because the recordings are not on the CD:
  - three death messages;
  - Franz's introduction and one of his rumour lines;
  - eight of Bonehead's lines, which scroll past too quickly with speech on (turn speech off to read them).

  These cannot be fixed without new recordings.
- The "Battered By Badders" death exists, but nothing in the game triggers it.

**Fixed here that Enhanced 1.2 listed as known issues:**
- the Vorpal Bunny at the right edge;
- the Fighter door on the character-select screen;
- the revenant's kopeks;
- oiling one castle door also counting for the other doors (fixed in every castle room with lockable doors, as far as we know);
- probably "save rot": its most likely cause is fixed, but this is not proven (see section 5).

## 8. Reporting a problem

Please include:
- whether you used DOSBox (and your cycles setting) or ScummVM (and its version);
- what you did just before the problem, step by step;
- the fix name in [brackets] from section 6, if it looks related;
- a saved game from just before the problem, if you have one.

Where to report: the Issues tab of this patch's GitHub page, https://github.com/HeroRoger/QFG4-Enhanced/issues

## 9. Credits

This pack is built on AshLancer's and DoomLazer's work. Thank you both, and thanks to everyone below.

- **Sierra On-Line**, and **Lori Ann Cole and Corey Cole**, who designed Quest for Glory IV: Shadows of Darkness (1993). Quest for Glory IV is copyright Sierra On-Line, Inc.; SIERRA is a trademark of Activision Publishing, Inc.
- **AshLancer** (Alex Abrahamian), author of QFG4 Enhanced Update 1.1, which restored cut audio, a cut encounter and many fixes.
- **DoomLazer**, author of Enhanced 1.2, which decompiled AshLancer's patches and fixed bugs they had introduced.
- **NewRisingSun**, whose speed fixes for this game are part of Enhanced.
- **The ScummVM team.** Many fixes in this patch are ScummVM's own QFG4 script fixes, copied byte for byte or rebuilt for DOSBox. ScummVM's bug tracker and notes were the map for much of this work. ScummVM is free software under the GNU GPL. Thanks also to **sluicebox**, who is credited in Enhanced 1.2 for QFG4 fix research.
- **h3rmit-git**, whose QFG4-Fixes patch (2022, https://github.com/h3rmit-git/QFG4-Fixes) fixed the jester's chair speed bug and the Squid Stone slope and bonsai crashes first. It is how we learned of the chair bug.
- The Quest for Glory fan community, for years of bug reports, walkthroughs and Let's Plays.
- This patch: **HeroRoger** (https://github.com/HeroRoger/QFG4-Enhanced).
- *The analysis and patch building were done with the help of an AI assistant (Claude, by Anthropic). Every fix is described in this file and was checked by automated tests.*

This patch is free, unofficial and not connected with Sierra, Activision or the Coles. You need your own copy of Quest for Glory IV (CD, GOG or Steam) and of QFG4 Enhanced 1.2. It is provided as is; keep backups of your game and your saves.

## 10. Version history

- 1.0 (2026-10-27): first release.
