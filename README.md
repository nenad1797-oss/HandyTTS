# Handy TTS

Local neural-net text-to-speech for Nuclear Option game chat: every player
gets a stable, distinct voice — same across servers, even if they change
their name. The voice stays the same, so you can disable the player-name
announcer at the beginning of every line and just recognize players by their
voices. Runs fully offline on your PC, fully CPU, negligible performance
impact.

Pick **Handy TTS Lite** instead if you want the game's own voice, just faster
and cleaner, with zero downloads beyond kilobytes. Only ever run one of them.

## What it does

- Speaks chat lines with a local neural voice (904 voices) instead of the
  stock voice — randomly assigned to players, or assigned by you —
  suppressing the game's own speech while enabled.
- Remembers each player by SteamID: stable voice, mute, and rename across
  servers and sessions.
- Says who is talking (`<name> says:`) if enabled, with a separate announcer
  voice that stays quiet unless the speaker is new or 20 seconds passed, so
  you don't hear "name says:" every 2 seconds when someone spams. Turn the
  announcer off entirely and identify players by voice alone.
- Fixes chat slang/typos before speaking (`expansions.txt`, editable) and
  pronounces game terms right (`pronounce.txt`, editable). Chat on screen is
  never touched.
- Speeds up when needed so speech catches up with chat; never drops messages.
- Scoreboard right-click per player: Assign TTS voice / Mute TTS voice /
  Rename TTS voice (shown in-game as Assign TTS / Mute TTS / Rename TTS).
- Chat commands: `/tvoice /tmute /tunmute /tname /thelp`.
- Speech audit log of everything spoken (see Bug reports).

## Install

- **NOMM (recommended):** install from the Nuclear Option Mod Manager listing.
- **Manual:** extract the release zip into a new folder
  `BepInEx/plugins/Com.MrNoHands.TtsExpander/` next to the game, so the DLL,
  the native libraries, and `data/` sit together. Launch the game.

## Options (F1 config menu)

**General**
- Enabled — master switch. Off = mod fully idle, game speech behaves stock.
- SpeakOwnDev — also speak your own messages (off by default; mostly for
  testing your setup).
- LogLevel — 0 = errors only, 1 = normal, 2 = per-message debug trace.
  Set to 2 only when collecting a bug report, then back to 1.

**Voice**
- AnnounceNames — speak `<name> says:` before lines (on by default). Turn it
  OFF to play announcer-free: every player keeps their own stable voice, so
  you learn who's talking by sound alone.
- AnnouncerSid — which of the 904 voices reads the names (0–903, default 1).
- Speed — base speaking rate, 0.5–2 (default 1).
- Volume — our own output gain, 0–2 (2 = 200%).
- Noise — phoneme randomness, 0–1.5 (default 0.5; lower = steadier voice).
- Variation — expressiveness variation, 0–1.5 (default 1).
- Pauses — pause length at punctuation, 0–1 (default 1).
- OwnSid — your own voice, -1 = automatic (range -1–903).

**Queue**
- CatchUpSec — how many seconds of speech backlog before the rate ramps up
  to catch up (2–30, default 3).

**Storage**
- LogDays — keep the speech audit log this many days, 0–30 (default 7,
  0 = off).
- PruneDays — forget players unseen for this many days, 0–3650
  (default 1825 = 5 years, 0 = never).
- ModelDir — Piper model folder; empty = the `data/` folder next to the DLL.

## Bug reports

Set F1 → LogLevel = 2, reproduce, then send:

1. `Steam\steamapps\common\Nuclear Option\BepInEx\LogOutput.log`
2. `BepInEx\config\Com.MrNoHands.TtsExpander\tts-log.txt`

Set LogLevel back to 1 afterwards. `tts-log.txt` contains chat text you heard
plus player names — only share it if you are comfortable sharing that session.

## Known issues (v1.0.0)

- **Rename popup vs chat focus:** while typing a name in the Rename TTS
  popup, pressing SPACE or `-` hands focus to the game chat and the popup
  can't be refocused. Use one-word names for now (no spaces or dashes); if
  chat steals focus, close it and reopen the menu. Fix planned.
- **Short own-message echo:** very short own messages (under 6 characters)
  are occasionally spoken twice (your send + the server echo). Minor; fix
  planned.
- **No voices at all:** check `LogOutput.log` for `Piper engine failed` — you
  likely need the Microsoft Visual C++ Redistributable (x64), free from
  Microsoft. Install it, relaunch, done.

## Build from source

`dotnet build -c Release` (needs the game's DLLs; see HintPaths in the
csproj). Same source also builds Handy TTS Lite with `-c ReleaseLite`.

## Credits

Our code is MIT (see `LICENSE`). Voice engine, voice model, and runtime are
third-party — see `CREDITS.md`. No user-side license steps required.
