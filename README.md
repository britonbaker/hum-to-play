# Hum to Play

Hum into your mic and watch a violin play it, right in the browser.

- `index.html`: hum to play the violin.
- `conductor.html`: Conductor Mode. Talk to the whole orchestra, one section or one player, hum a tune and they play along in harmony, and ask Clef for ideas.

Everything runs on your device. The mic needs the page on https, which GitHub Pages provides.

## Instrument sounds

Conductor Mode plays physical models in an AudioWorklet: the violins and cellos are bowed-string waveguides with a bow friction curve and a body resonance, the flute is a jet and bore waveguide (both after the Synthesis ToolKit), and the brass is additive synthesis that gets brighter as it gets louder. Add `?sound=classic` to the address to hear the older synth voices.

## Sung ideas

Tap Listen, talk, and sing the part you mean: "make the violins go like *this*". Every word comes back tagged with its notes, loudness and length, and the orchestra plays the sung part. Voice memos work the same way.

Agents can read the same record:

- `window.humToPlay.lastIdea` and `window.humToPlay.onIdea(fn)`
- a `sungidea` event on `window`
- the Copy sung idea button (JSON)

Each idea looks like `{ format: "hum-to-play/sung-idea@1", text, timing, words: [{ text, start, end, dur, sung, pitch: { note, midi, hz }, volume: { db, level }, notes: [...] }], sung_words, melody: [{ note, midi, start, dur, word }] }`. Times are in seconds from the start of the recording.
