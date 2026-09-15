# Handy TTS

Local neural text-to-speech for Nuclear Option game chat: every player gets a
stable, distinct voice. Runs fully offline on your PC — no accounts, no cloud.

Pick **Handy TTS Lite** instead if you want the game's own voice, just faster
and cleaner, with zero downloads beyond kilobytes. Only ever run one of them.

## What it does

- Speaks chat lines with a local neural voice (904 speakers) instead of the
  stock voice, suppressing the game's own speech while enabled.
- Remembers each player by SteamID: stable voice, mute, and rename across
  servers and sessions.
- Says who is talking (`<name> says:`) with a separate announcer voice that
  stays quiet unless the speaker is new or 20 seconds passed.
- Fixes chat slang/typos before speaking (`expansions.txt`, editable) and
  pronounces game terms right (`pronounce.txt`, editable). Chat on screen is
  never touched.
- Speeds up under flood so speech catches up with chat; never drops messages.
- Scoreboard right-click: Assign TTS / Mute TTS / Rename TTS per player.
- Chat commands: `/tvoice /tmute /tunmute /tname /thelp`.
- Speech audit log of everything spoken (see Bug reports).

## Install

- **NOMM (recommended):** install from the Nuclear Option Mod Manager listing.
- **Manual:** extract the release zip into a new folder
  `BepInEx/plugins/Com.MrNoHands.TtsExpander/` next to the game, so the DLL,
  the native libraries, and `data/` sit together. Launch the game.

## Options (F1 config menu)

General: Enabled, SpeakOwnDev (hear your own lines), LogLevel.
Voice: Announce, AnnouncerSid (0–903), Speed, Volume (own gain), Noise,
Variation, Pauses, OwnSid (-1 = automatic).
Queue: CatchUpSec. Storage: ModelDir, PruneDays, LogDays.

## Bug reports

Set F1 → LogLevel = 2, reproduce, then send:

1. `Steam\steamapps\common\Nuclear Option\BepInEx\LogOutput.log`
2. `BepInEx\config\Com.MrNoHands.TtsExpander\tts-log.txt`

Set LogLevel back to 1 afterwards. `tts-log.txt` contains chat text you heard
plus player names — only share it if you are comfortable sharing that session.

## Build from source

`dotnet build -c Release` (needs the game's DLLs; see HintPaths in the
csproj). Same source also builds Handy TTS Lite with `-c ReleaseLite`.

## Credits

Our code is MIT (see `LICENSE`). Voice engine, voice model, and runtime are
third-party — see `CREDITS.md`. No user-side license steps required.
