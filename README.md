# OpenMW Standalone VR

[![OpenMW-XR Standalone VR (Meta Quest 3) Proof of Life](<img width="853" height="480" alt="image" src="https://github.com/user-attachments/assets/83f870a2-ebce-4f22-9ee7-f5d3d20d9d6c" />)](https://www.youtube.com/watch?v=39rUsiT9f3E)

## Background

Some time ago, we ran a community poll asking which classic game people most wanted to see brought to standalone VR. The clear winner was **The Elder Scrolls III: Morrowind**, courtesy of the OpenMW project.

Following that result, we began discussions with the OpenMW team to better understand how we could utilise their project. OpenMW is an extraordinary open source effort that has been developed and maintained over many years by a dedicated group of contributors. Their work has ensured that Morrowind remains playable and accessible on modern platforms long after its original release.

As those discussions progressed, it became clear that properly supporting OpenMW in a way that respected their development process would require a significant long-term commitment to maintaining and upstreaming changes. It would also limit our ability to alter underlying gameplay systems where necessary to create the best possible VR experience.

While we have tremendous respect for that approach, it ultimately did not align particularly well with how Team Beef operates.

Our community supports us because we focus on bringing classic games to VR and delivering playable results within a relatively short timeframe, typically working on projects that are already feature-complete. Committing to a large, ongoing upstream development effort would inevitably mean spending less time working on the ports and projects our supporters expect us to create. We're only a small team with limited bandwidth.

This was not a disagreement with the OpenMW team's goals or methods. Rather, it was simply a recognition that both projects have different priorities and different measures of success.

As a result, we decided to pursue other porting opportunities until a workable path forward could be found.

---

## Why This Repository Exists

That decision, however, never completely sat right with us.

Morrowind remains one of the most requested experiences from our community, and we would love players to have a straightforward way to enjoy it on standalone VR headsets. OpenMW continues to be a hugely successful project, and we'd love to help bring it to a new audience.

This repository is therefore intended as a downstream fork of OpenMW. Its purpose is not to become the primary OpenMW project, nor is it intended to serve as a long-term fork that regularly pushes changes upstream.

Instead, the goal is simple:

> **Get Morrowind running on standalone VR hardware as quickly and reliably as possible while applying the VR improvements and adaptations we have developed across previous projects.**

Our focus is on creating a practical standalone VR experience rather than establishing a new branch of OpenMW development.

---

## Project Structure

At a high level, this project combines three existing pieces of work alongside our own experience in VR conversions, OpenXR, and rendering.

### 1. OpenMW

https://github.com/OpenMW

At its core is the OpenMW engine itself (currently based on **0.51**).

OpenMW represents the overwhelming majority of the work that makes this project possible. Years of development by OpenMW contributors have produced a modern, open source reimplementation of the Morrowind engine that serves as the foundation for everything here.

Our intention is to keep VR-specific changes isolated wherever practical through conditional compilation and clearly separated code paths, with the hope that staying reasonably current with future OpenMW releases remains straightforward.

### 2. The Existing PCVR Implementation

https://gitlab.com/madsbuvi/openmw

The second major component is the existing PCVR implementation by **Mads Buvik Sandvei**.

This project provides many of the VR-specific concepts, interactions, and approaches that the standalone version can learn from.

We recognise that the PCVR implementation has evolved significantly since the snapshot used as a reference here, particularly through the introduction of newer Lua-based systems and additional improvements. As a result, this repository should not be viewed as a reflection of the current state of the PCVR project.

Instead, it serves as a reference point from which we can incorporate useful ideas alongside our own solutions and approaches.

### 3. The Existing Android Fork

https://gitlab.com/modding-openmw/openmw-android-docker

The third component is the Android fork that provided the foundation for running OpenMW on Android-based systems.

The original Android fork relied heavily on Docker as part of its build process. While Docker is a powerful solution, it also introduces additional setup requirements that can create a significant barrier to entry for contributors.

To simplify development, we have removed the Docker dependency and migrated the build process toward a more traditional Windows-based workflow. Our intention is that developers should be able to clone the repository, install the required dependencies, and begin building without needing to learn or maintain a separate container environment.

This mirrors the workflow used across our other standalone VR projects.

---

## Current Status

The project currently consists of two primary components packaged together as a single application.

The first is a customised version of Duron27's Android launcher, presented as a traditional 2D interface. This has been adapted specifically for the standalone VR experience and includes a number of enhancements intended to simplify setup and game management for VR users.

Once configuration is complete, the launcher starts the main engine as a VR application using an Android intent, providing a seamless transition from setup into gameplay while remaining part of a single packaged experience.

From a technical standpoint, the project is already in a promising state:

- The game loads and runs in VR
- Environments can be explored
- Player movement is functional
- World interaction is operational

With that foundation now established, we consider the project to have entered the phase where the majority of the work begins.

The focus moving forward will be on refining the experience through:

- VR-specific gameplay improvements
- Interaction systems
- User interface enhancements
- Performance optimisation
- Platform integration
- Quality-of-life improvements

The road ahead remains substantial, but we now have a solid foundation upon which to build.

---

## The OpenMW Project & Next Steps

Before investing significantly more time, our first step will be to reach out to the OpenMW team and ensure they are comfortable with this endeavour. We would prefer to have that conversation before fully committing to the project.

The overwhelming majority of the work that makes this possible has already been done by OpenMW contributors. Their dedication, technical expertise, and years of effort deserve both recognition and respect.

We want to be absolutely clear:

> This project exists because of their work.

If you are interested in the continued development of OpenMW itself, we strongly encourage you to support and follow the main project.

---

## Project Goals

- Bring Morrowind to standalone VR headsets
- Maintain a practical, self-contained VR-focused codebase
- Keep future OpenMW integration as straightforward as reasonably possible
- Deliver a high-quality standalone VR experience

---

## What This Project Is Not

This project is **not**:

- An official OpenMW project
- A replacement for OpenMW
- A commitment that standalone Android VR changes will be upstreamed
- A competing branch of OpenMW development

This is simply our attempt to make one of gaming's greatest RPGs playable in standalone VR while showing proper respect to the people who made that possibility a reality.

---

# FAQ

## Will this stay up to date with OpenMW engine progress?

The changes to the underlying engine are relatively modest compared to the size of OpenMW itself. As a result, we hope future OpenMW improvements can be merged into this project where appropriate.

The project is currently based on **OpenMW 0.51**.

## Will this stay up to date with Android launcher changes?

The launcher has already diverged significantly in order to support the VR experience and associated workflows.

For that reason, it is now considered a separate project. Duron27 has done a fantastic job providing a stable Android foundation, and we would like to thank them for their efforts.

The launcher architecture should also make future mod support relatively straightforward.

## In what ways will this resemble the PCVR implementation?

The PCVR version introduced many excellent solutions for user interfaces, interactions, and VR-specific gameplay challenges.

It is fair to say that very little of the original PCVR code currently exists in our implementation, as we have already replaced major rendering components with systems more closely aligned with our previous standalone VR releases.

However, we absolutely intend to draw inspiration from many of the excellent ideas developed by the PCVR project while combining them with our own approaches.

## What is performance like?

Performance is currently promising.

- Indoor environments generally perform well and are comfortably playable.
- Outdoor environments remain more challenging but are already playable with some settings adjustments.

We have not yet implemented optimisations such as Multiview rendering or various performance improvements used in our other standalone ports, so we remain cautiously optimistic that performance will improve significantly as development continues.

## How can I download this? Will in-development versions be behind a paywall?

No.

Development builds and releases will be distributed through this repository and other public channels when appropriate.

You are welcome to follow development through our Patreon, where we may occasionally post development logs and progress updates, but access to the project itself will remain open throughout development in the spirit of the OpenMW project.

## Will the gameplay remain faithful to the original game?

This is one area where our approach may differ somewhat from the core OpenMW project.

As with our previous VR ports, we believe certain gameplay systems that work well on a flat screen do not necessarily translate perfectly into virtual reality.

Where appropriate, we may adapt gameplay systems to improve comfort, usability, immersion, or overall playability in VR. Wherever possible, we will attempt to place these changes behind optional settings labelled as VR-specific enhancements.

Our goal remains the same as it has been for all of our Flat2VR projects:

> Preserve the original game as faithfully as possible while making it feel like a native VR experience.

Original Readme:

OpenMW
======

OpenMW is an open-source open-world RPG game engine that supports playing Morrowind by Bethesda Softworks. You need to own the game for OpenMW to play Morrowind.

OpenMW also comes with OpenMW-CS, a replacement for Bethesda's Construction Set.

* Version: 0.52.0
* License: GPLv3 (see [LICENSE](https://gitlab.com/OpenMW/openmw/-/raw/master/LICENSE) for more information)
* Website: https://www.openmw.org
* IRC: #openmw on irc.libera.chat
* Discord: https://discord.gg/bWuqq2e


Font Licenses:
* DejaVuLGCSansMono.ttf: custom (see [files/data/fonts/DejaVuFontLicense.txt](https://gitlab.com/OpenMW/openmw/-/raw/master/files/data/fonts/DejaVuFontLicense.txt) for more information)
* DemonicLetters.ttf: SIL Open Font License (see [files/data/fonts/DemonicLettersFontLicense.txt](https://gitlab.com/OpenMW/openmw/-/raw/master/files/data/fonts/DemonicLettersFontLicense.txt) for more information)
* MysticCards.ttf: SIL Open Font License (see [files/data/fonts/MysticCardsFontLicense.txt](https://gitlab.com/OpenMW/openmw/-/raw/master/files/data/fonts/MysticCardsFontLicense.txt) for more information)

Current Status
--------------

The main quests in Morrowind, Tribunal and Bloodmoon are all completable. Some issues with side quests are to be expected (but rare). Check the [bug tracker](https://gitlab.com/OpenMW/openmw/-/issues/?milestone_title=openmw-1.0) for a list of issues we need to resolve before the "1.0" release. Even before the "1.0" release, however, OpenMW boasts some new [features](https://wiki.openmw.org/index.php?title=Features), such as improved graphics and user interfaces.

Pre-existing modifications created for the original Morrowind engine can be hit-and-miss. The OpenMW script compiler performs more thorough error-checking than Morrowind does, meaning that a mod created for Morrowind may not necessarily run in OpenMW. Some mods also rely on quirky behaviour or engine bugs in order to work. We are considering such compatibility issues on a case-by-case basis - in some cases adding a workaround to OpenMW may be feasible, in other cases fixing the mod will be the only option. If you know of any mods that work or don't work, feel free to add them to the [Mod status](https://wiki.openmw.org/index.php?title=Mod_status) wiki page.

Getting Started
---------------

* [Official forums](https://forum.openmw.org/)
* [Installation instructions](https://openmw.readthedocs.io/en/latest/manuals/installation/index.html)
* [Build from source](https://wiki.openmw.org/index.php?title=Development_Environment_Setup)
* [Testing the game](https://wiki.openmw.org/index.php?title=Testing)
* [How to contribute](https://wiki.openmw.org/index.php?title=Contribution_Wanted)
* [Report a bug](https://gitlab.com/OpenMW/openmw/issues) - read the [guidelines](https://wiki.openmw.org/index.php?title=Bug_Reporting_Guidelines) before submitting your first bug!
* [Known issues](https://gitlab.com/OpenMW/openmw/issues?label_name%5B%5D=Bug)

The data path
-------------

The data path tells OpenMW where to find your Morrowind files. If you run the launcher, OpenMW should be able to pick up the location of these files on its own, if both Morrowind and OpenMW are installed properly (installing Morrowind under WINE is considered a proper install).

Command line options
--------------------

    Syntax: openmw <options>
    Allowed options:
      --config arg                          additional config directories
      --replace arg                         settings where the values from the
                                            current source should replace those
                                            from lower-priority sources instead of
                                            being appended
      --user-data arg                       set user data directory (used for
                                            saves, screenshots, etc)
      --resources arg (=resources)          set resources directory
      --help                                print help message
      --version                             print version information and quit
      --data arg (=data)                    set data directories (later directories
                                            have higher priority)
      --data-local arg                      set local data directory (highest
                                            priority)
      --fallback-archive arg (=fallback-archive)
                                            set fallback BSA archives (later
                                            archives have higher priority)
      --start arg                           set initial cell
      --content arg                         content file(s): esm/esp, or
                                            omwgame/omwaddon/omwscripts
      --groundcover arg                     groundcover content file(s): esm/esp,
                                            or omwgame/omwaddon
      --no-sound [=arg(=1)] (=0)            disable all sounds
      --script-all [=arg(=1)] (=0)          compile all scripts (excluding dialogue
                                            scripts) at startup
      --script-all-dialogue [=arg(=1)] (=0) compile all dialogue scripts at startup
      --script-console [=arg(=1)] (=0)      enable console-only script
                                            functionality
      --script-run arg                      select a file containing a list of
                                            console commands that is executed on
                                            startup
      --script-warn [=arg(=1)] (=1)         handling of warnings when compiling
                                            scripts
                                            0 - ignore warnings
                                            1 - show warnings but consider script as
                                            correctly compiled anyway
                                            2 - treat warnings as errors
      --load-savegame arg                   load a save game file on game startup
                                            (specify an absolute filename or a
                                            filename relative to the current
                                            working directory)
      --skip-menu [=arg(=1)] (=0)           skip main menu on game startup
      --new-game [=arg(=1)] (=0)            run new game sequence (ignored if
                                            skip-menu=0)
      --encoding arg (=win1252)             Character encoding used in OpenMW game
                                            messages:

                                            win1250 - Central and Eastern European
                                            such as Polish, Czech, Slovak,
                                            Hungarian, Slovene, Bosnian, Croatian,
                                            Serbian (Latin script), Romanian and
                                            Albanian languages

                                            win1251 - Cyrillic alphabet such as
                                            Russian, Bulgarian, Serbian Cyrillic
                                            and other languages

                                            win1252 - Western European (Latin)
                                            alphabet, used by default
      --fallback arg                        fallback values
      --no-grab [=arg(=1)] (=0)             Don't grab mouse cursor
      --export-fonts [=arg(=1)] (=0)        Export Morrowind .fnt fonts to PNG
                                            image and XML file in current directory
      --activate-dist arg (=-1)             activation distance override
      --random-seed arg (=<impl defined>)   seed value for random number generator
