# Quest for Glory IV Bug Fix Patch (QFG4 Fix Pack)

**121 bug fixes for Quest for Glory IV: Shadows of Darkness**, on top of QFG4 Enhanced 1.2. For the CD version in English, which is also the version GOG and Steam sell. Works in DOSBox and ScummVM.

**Download:** [latest release](https://github.com/HeroRoger/Quest-for-Glory-4-Bug-Fix-Patch/releases/latest) (QFG4-FixPack-1.0.zip)

## What it fixes

- **26 crashes**, for example:
  - walking up, walking down or sliding on the slippery slope at the Standing Squid Stone;
  - throwing rocks at the rock pile by the bonsai;
  - the necrotaurs capturing you in the forest;
  - "Not an Object" errors after using Fetch.
- **24 lockups**, where the game keeps running but you can't do anything (for example in the bone cage, or throwing when you have exactly two daggers).
- **7 dead ends**, where you could no longer finish the game (for example the Domovoi, and the monastery fire).
- **64 other bugs**, including timing problems on fast PCs. The game now runs at most 60 frames per second, so spells, the Vorpal Bunny and combat no longer run too fast in DOSBox, and you no longer need to slow DOSBox down for combat.

It changes no art, music, voices or story.

Every fix is explained in [README_FIXPACK.md](https://github.com/HeroRoger/Quest-for-Glory-4-Bug-Fix-Patch/blob/main/README_FIXPACK.md).

## What you need

1. Quest for Glory IV, CD version in English (GOG, Steam or the original CD).
2. QFG4 Enhanced 1.2 by DoomLazer: [download it here](https://github.com/Doomlazer/QFG4-Enhanced/releases/tag/QFG4_Enhanced_v1.2) (QFG4.Enhanced.1.2.zip). Install it first; this patch does not work on its own.

## Installing (short version)

1. Back up your Quest for Glory IV game folder, or at least its `PATCHES` folder.
2. Install Enhanced 1.2: rename the game's old `PATCHES` folder (for example to `PATCHES_BAK`), then extract QFG4.Enhanced.1.2.zip into the game folder.
3. Extract QFG4-FixPack-1.0.zip into the same game folder and say yes when asked to overwrite. Keep Enhanced's `.hep` files.
4. GOG copies: if `PATCHES` has any other `.hep` file whose number matches one of this patch's `.scr` files (for example `803.hep`), move it into your backup.
5. Play. DOS saved games made with Enhanced 1.2 keep working. In ScummVM, start a new game.

The full guide, including Linux, macOS and `RESOURCE.CFG` notes, is in [README_FIXPACK.md](https://github.com/HeroRoger/Quest-for-Glory-4-Bug-Fix-Patch/blob/main/README_FIXPACK.md), section 2.

**DOSBox tip:** use `cycles=max`.

## Testing

Every fix was checked by automated tests, and many were tried in DOSBox and ScummVM. The whole game has not been played start to finish with this patch yet, so keep backups of your game and your saves.

Found a problem? Please report it on the [Issues](https://github.com/HeroRoger/Quest-for-Glory-4-Bug-Fix-Patch/issues) tab.

## Credits

Built on QFG4 Enhanced by **AshLancer** (Enhanced 1.1) and **DoomLazer** (Enhanced 1.2). Many fixes are the **ScummVM team's** own QFG4 script fixes, rebuilt for DOSBox. Thanks also to NewRisingSun, sluicebox, h3rmit-git and the Quest for Glory fan community. Full credits: README_FIXPACK.md, section 9.

Made by HeroRoger with the help of an AI assistant (Claude, by Anthropic). Quest for Glory IV is copyright Sierra On-Line. This free, unofficial patch is not connected with Sierra, Activision or the Coles.

The README.txt in this repository is DoomLazer's readme for Enhanced 1.2 (this repository started as a copy of theirs).
