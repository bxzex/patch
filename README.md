# Patch

A modular synthesiser in the browser. Drag modules around the rack, pull cables
between jacks, and the Web Audio graph rewires itself underneath you while it
runs.

Live: https://bxzex.github.io/patch/

## Why the cables are real

Every cable is an actual connection in the audio graph, control voltage
included. An audio jack calls `connect(node)`. A CV jack calls `connect(param)`
against the `AudioParam` it modulates, which is the browser's equivalent of
patching voltage into a knob: the signal is summed onto the parameter rather
than replacing it, exactly like hardware. Cutting a cable calls `disconnect`
with the same target, so the path breaks immediately and the sound stops.

Triggers are the exception. A gate has no audio-rate representation worth
sending, so trigger cables are scheduled in JavaScript against `currentTime`
and drawn dashed yellow to make the difference visible.

## Modules

Oscillator, Noise, LFO, Filter, VCA, Envelope, Clock, Sequencer, Delay, Reverb
and Output. The envelope is a `ConstantSourceNode` with a scheduled ADSR, which
is the cleanest CV generator the API offers. The reverb builds its own impulse
response from decaying noise at load, so there is no file to fetch. The
sequencer emits cents into an oscillator's detune, so the pitch knob stays the
root and the pattern transposes with it.

Four presets are wired and ready: an init patch, an acid line with a resonant
filter sweep, a drone, and a bell. Shift click or right click a sequencer step
to change its pitch.

## Notes

One HTML file. No libraries. Modules are DOM, cables are SVG, and audio is the
Web Audio API. Nothing is recorded or uploaded.

Built by [bxzex](https://bxzex.com).
