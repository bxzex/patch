# Patch

A modular synth in the browser. Drag modules around the rack and pull cables between the jacks.

https://bxzex.github.io/patch/

Every cable is a real Web Audio connection. Audio jacks connect to nodes, and CV jacks connect to the AudioParam they modulate, so the signal adds onto the knob the same way it would on hardware. Pull a cable out and the connection is actually gone. Triggers are the one exception. They're scheduled in JS and drawn as dashed yellow cables.

The modules are oscillator, noise, LFO, filter, VCA, envelope, clock, sequencer, delay, reverb and output. There are four presets to start from. Shift-click a sequencer step to change its pitch.
