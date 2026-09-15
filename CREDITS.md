# Credits — third-party components shipped with Handy TTS

Our own code in this repo is MIT (see `LICENSE`). The release archive
additionally ships the following third-party components, which remain under
their own licenses:

- **Piper** (GPL-3.0) — neural text-to-speech engine and the
  `en_US-libritts_r-medium` voice model format.
  https://github.com/rhasspy/piper
- **espeak-ng** (GPL-3.0) — phonemization data (`espeak-ng-data`).
  https://github.com/espeak-ng/espeak-ng
- **Sherpa-ONNX** (Apache-2.0) — the runtime that runs the voice model
  (`sherpa-onnx.dll`, `onnxruntime.dll`).
  https://github.com/k2-fsa/sherpa-onnx
- **Voice model** `en_US-libritts_r-medium` (904 speakers) from the
  piper-voices collection.
  https://github.com/rhasspy/piper-voices

We ship Sherpa-ONNX binaries running a Piper-format voice file plus
espeak-ng data files. We do not ship Piper or espeak-ng program code.
No user-side license steps are required.
