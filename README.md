# Lofi-music-creator
--------------------------------------------------------------------------------
                         LOFI STUDIO v2 — README
                   Browser-Based Lo-Fi Audio Processor
--------------------------------------------------------------------------------

  beats · reverb · ambient overlays · smart auto-tune · trim · export
  Built entirely with HTML + Web Audio API. No server. No uploads. Just you.

--------------------------------------------------------------------------------
  WHAT IS THIS?
--------------------------------------------------------------------------------

LOFI STUDIO v2 is a fully browser-based audio processing tool that transforms
any song into a lo-fi, slowed & reverbed, or vaporwave version — right inside
your browser tab. No installation required. No internet needed after opening
the file. Your audio never leaves your device.

It was built using the Web Audio API, which gives access to real-time audio
effects like convolution reverb, biquad filters, waveshaping, and oscillator-
based drum synthesis — all running locally on your machine.

--------------------------------------------------------------------------------
  HOW TO USE
--------------------------------------------------------------------------------

1. Open the file "lofi-studio-v2.html" in any modern browser
   (Chrome, Edge, or Firefox recommended).

2. Drag and drop your song onto the drop zone, or click it to browse.
   Supported formats: MP3, WAV, OGG, FLAC (recommended max ~50MB).

3. Choose a preset or hit "Analyze" to auto-tune the settings for your song.

4. Adjust beats, ambient overlays, and fine-tune controls to your taste.

5. Hit Play to preview. When satisfied, click Export to download your mix.

--------------------------------------------------------------------------------
  FEATURES
--------------------------------------------------------------------------------

  [1] SIX PRESETS
  ---------------
  Ready-made effect combinations optimized for different vibes:

    Lo-Fi       -- Warm, nostalgic, slightly muffled. Classic lo-fi feel.
    Slowed      -- Dreamy drift. Slows the song significantly.
    Reverb      -- Large hall-like space. Maximum echo and width.
    Vaporwave   -- Slowed + pitched down + heavy reverb. Dreamy 80s feel.
    Bedroom Pop -- Very muffled, close, intimate. Like through a wall.
    Original    -- No effects applied. Clean playback.


  [2] SMART AUTO-TUNE (Analyze Button)
  -------------------------------------
  Click "Analyze" after loading a song. The engine will:

    - Sample the song's frequency spectrum (low / mid / high energy)
    - Detect the approximate BPM via onset detection
    - Calculate the ideal reverb depth, low-pass filter frequency,
      bass boost, warmth cut, saturation, stereo width, and playback speed
      based on the spectral characteristics of that specific song
    - Auto-sync the beat sequencer BPM to the detected tempo

  Songs with heavy high-frequency content get more aggressive filtering.
  Songs with deep low-end get more reverb and bass warmth applied.


  [3] FINE TUNE CONTROLS
  -----------------------
  8 sliders for complete manual control:

    Speed           -- Playback rate (0.5x to 1.0x). Slowing = lower pitch.
    Reverb Mix      -- Wet/dry mix of the convolution reverb (0-100%).
    Low-Pass Filter -- Cuts frequencies above this value (500Hz-20kHz).
                       Lower = more muffled lo-fi character.
    Vinyl Crackle   -- Adds procedural vinyl pop and hiss noise (0-100%).
    Bass Boost      -- Low-shelf EQ gain at 200Hz (-6dB to +12dB).
    Warmth (Hi-Cut) -- High-shelf EQ cut at 4kHz (-12dB to 0dB).
                       Reduces harshness and adds warmth.
    Stereo Width    -- Expands or narrows the stereo image (0-100%).
    Saturation      -- Soft tape-style harmonic distortion (0-100%).
                       Adds analog warmth without clipping.


  [4] BEAT ENGINE
  ---------------
  Adds synthesized drums directly into your mix, synced to BPM.

  Beat Styles:
    Lo-Fi Boom Bap  -- Classic hip-hop kick/snare pattern. Lo-fi staple.
    Trap Hi-Hats    -- Rapid hi-hat rolls with offbeat kicks. Trap energy.
    EDM Kick        -- Four-on-the-floor kick pattern. Dance floor ready.
    Jazz Brush      -- Loose, swinging brush pattern. Cafe jazz vibes.
    No Beats        -- Disable all drums entirely.

  Step Sequencer:
    A 16-step grid for Kick, Snare, Hi-Hat, and Percussion. Click any
    cell to toggle it on or off. Customize the beat pattern freely.
    Changes take effect immediately during playback.

  BPM Slider:
    Manually set the tempo from 60 to 180 BPM.
    After using Analyze, this auto-sets to 85% of detected song BPM
    for a relaxed lo-fi feel.

  Beat Volume:
    Controls the overall drum level in the mix.


  [5] AMBIENT SOUND OVERLAYS
  ---------------------------
  Procedurally generated ambient layers you can mix into any song.
  Each has its own volume slider and can be toggled independently.

    Rain      -- Pink noise band-passed to simulate rainfall texture.
    Thunder   -- Low-frequency rumble with occasional crackle bursts.
    Forest    -- Modulated high-frequency noise simulating wind and birds.
    Cafe      -- Low-frequency murmur with subtle conversation texture.
    Fireplace -- Low-pass noise with random pops. Warm and crackling.
    Vinyl     -- High-frequency hiss and crackle. Classic record player.
    Wind      -- Slowly modulated band-pass noise. Breezy and spacious.
    City Night-- Distant low rumble with faint ambient city sounds.

  TIP: Rain at 15-25% volume with Lo-Fi preset = incredibly cozy.
  TIP: Vinyl + Fireplace together = perfect late-night study session sound.

  All active ambients are included when you export.


  [6] TRIM
  --------
  Cut your song to any section before exporting.

    - Switch to the "Trim" tab to see the waveform of your loaded song.
    - Drag the left handle  to set the start (In) point.
    - Drag the right handle to set the end (Out) point.
    - The highlighted region shows what will be exported.
    - Click "Preview Trim" to play just that section.
    - Click "Reset Trim" to restore the full song length.
    - Use "Export Trimmed" to download only the trimmed section.


  [7] PLAYBACK CONTROLS
  ----------------------
    Restart      -- Jump back to the beginning.
    Skip Back    -- Go back 5 seconds.
    Play/Pause   -- Start or pause playback.
    Skip Forward -- Jump ahead 5 seconds.
    Stop         -- Stop and reset position.

  Click anywhere on the progress bar to seek to that position.


  [8] EXPORT
  ----------
  Two export options, both render a full WAV file offline:

    Export Full Mix   -- The entire song with all effects applied.
    Export Trimmed    -- Only the trimmed section with all effects applied.

  The export includes: speed change, reverb, filter, crackle, bass, warmth,
  saturation, all active beats, and all active ambient overlays.

  Output format: WAV (uncompressed, 44100Hz, 16-bit stereo).
  File names: "lofi-full-mix.wav" or "lofi-trimmed.wav"

--------------------------------------------------------------------------------
  AUDIO EFFECTS -- HOW THEY WORK
--------------------------------------------------------------------------------

  Speed / Pitch
    Uses BufferSource.playbackRate. Slowing the playback rate also lowers
    the pitch naturally, exactly like playing a cassette slower -- no
    artificial pitch correction. This is what gives slowed songs that deep,
    warm, underwater quality.

  Reverb
    Convolution reverb using a synthesized impulse response. The IR is a
    decaying noise burst that simulates a large room's reflections. The
    wet/dry mix determines how much of the reverbed signal is blended in.

  Low-Pass Filter
    A biquad low-pass filter that cuts frequencies above the set value.
    At 2-4kHz, it gives that classic muffled lo-fi sound as if the music
    is playing from another room or an old tape.

  Bass Boost
    Low-shelf EQ boost at 200Hz. Adds weight and warmth to the low end
    without muddying the sub-bass.

  Warmth (Hi-Cut)
    High-shelf EQ cut at 4kHz. Removes harshness and digital sharpness.
    Combined with the low-pass filter, this creates a smooth, analog feel.

  Saturation
    A soft-clipping waveshaper using a sinh-approximated curve. Adds
    harmonic overtones similar to tape saturation. Keeps the sound warm
    without distorting.

  Vinyl Crackle
    A noise buffer with randomized amplitude spikes (probability-based pops)
    mixed at low gain. Simulates the surface noise of a vinyl record.

  Beat Synthesis
    Drums are synthesized from scratch using oscillators and noise buffers:
    - Kick:  Sine wave with fast frequency downward sweep (150Hz to 40Hz)
    - Snare: Triangle wave + bandpass-filtered white noise
    - Hi-Hat: Highpass-filtered white noise (above 8kHz), very short envelope
    - Perc:  Bandpass-filtered noise around 1200Hz

  Ambient Synthesis
    All ambient sounds are generated from noise buffers shaped with filters:
    - Pink noise (Voss algorithm) for rain
    - Low-frequency decay noise for thunder
    - Modulated high-pass noise for forest and wind
    - Bandpass-filtered noise with random tones for cafe
    All loops are seamless.

--------------------------------------------------------------------------------
  TIPS FOR THE BEST LO-FI RESULTS
--------------------------------------------------------------------------------

  For a classic lo-fi hip-hop feel:
    Preset: Lo-Fi  |  Beat: Lo-Fi Boom Bap  |  Ambient: Vinyl + Rain (15%)
    Speed: 0.85x   |  Filter: 2.5-3.0k      |  Reverb: 40-50%

  For slowed + reverb (TikTok / YouTube style):
    Preset: Slowed  |  Beat: None  |  Speed: 0.75x
    Reverb: 60-70%  |  Filter: 15k+  |  Warmth: -2 to -4dB

  For vaporwave / aesthetic:
    Preset: Vaporwave  |  Speed: 0.70x  |  Bass: +6dB
    Reverb: 65%        |  Filter: 5-6k  |  Saturation: 20-30%

  For night-drive / cinematic:
    Preset: Reverb  |  Ambient: City Night + Wind
    Width: 80%      |  Reverb: 75%  |  Filter: 12k

  For studying / focus:
    Preset: Lo-Fi  |  Ambient: Rain + Cafe  |  Beat: Lo-Fi Boom Bap at 30%
    Filter: 3k     |  Crackle: 25%          |  Speed: 0.9x

  Always click Analyze first -- it will get you 80% of the way there
  automatically, then you can fine-tune the rest.

--------------------------------------------------------------------------------
  BROWSER COMPATIBILITY
--------------------------------------------------------------------------------

  Fully supported:
    Google Chrome 80+     YES
    Microsoft Edge 80+    YES
    Firefox 76+           YES
    Brave                 YES

  Not recommended:
    Safari -- limited OfflineAudioContext support, export may not work
    Internet Explorer -- not supported

  Mobile: Works for playback on Chrome Android. Export may be slow on
  older phones due to offline rendering computation.

--------------------------------------------------------------------------------
  LIMITATIONS
--------------------------------------------------------------------------------

  - No pitch shifting independent of speed. Slowing = lower pitch (by design).
  - Export for long songs (above 10 min) may take 20-40 seconds to render.
  - Very large files (above 80MB) may cause memory issues on low-RAM devices.
  - Ambient sounds are synthesized and approximate; they are not recordings.
  - Beat synthesis is minimal; for complex beats, use an external DAW.
  - No MP3 export -- output is always uncompressed WAV. Use Audacity or
    any free converter (such as Convertio.co) to convert WAV to MP3 afterward.

--------------------------------------------------------------------------------
  FILE INFO
--------------------------------------------------------------------------------

  File:         lofi-studio-v2.html
  Size:         ~69 KB (single self-contained HTML file)
  Dependencies: Google Fonts (Bebas Neue, DM Mono, Fraunces) -- loaded from
                CDN on first open. Works fully offline after fonts are cached.
  No external libraries. No frameworks. Pure HTML + CSS + Web Audio API.

--------------------------------------------------------------------------------
  CREDITS
--------------------------------------------------------------------------------

  Built with the Web Audio API -- a browser-native audio processing standard.
  Drum synthesis techniques based on standard subtractive synthesis patterns.
  Pink noise generation uses the Voss-McCartney algorithm.
  Convolution reverb impulse response is synthesized, not a real room sample.

  Created by Sabharish using LOFI STUDIO -- a custom audio tool built with
  Claude (Anthropic). All audio processing happens locally in your browser.
  Your music stays on your device. Always.

