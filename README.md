# DAWGuitar
Allows user to use guitar for multiple instrumental types

## Overview

**Goal**: Allow a guitarist to plug into a Mac, play the guitar as if it were a drum/percussion instrument, and record layered patterns in real time.

- **Input**: Electric or mic’d acoustic guitar → audio interface → Mac.
- **Processing**: Detect transient events (string plucks, muted hits, palm strikes, etc.) and map them to per-track percussion sounds.
- **Output**: Audio playback through the Mac (no external MIDI/DAW routing required).
- **Recording**: Store project sessions with up to 12 tracks of triggered percussion patterns.
- **File Saving**: Save/load projects with track assignments, sound mappings, and recorded patterns.

---

## Features (Phase 1)

1. **Real-Time Audio Input**
   - Core Audio or AVAudioEngine for ultra-low latency capture.
   - Adjustable buffer size (default 64 samples, option for 32).
   - Input gain control.

2. **Transient Detection**
   - Detect amplitude spikes for trigger events.
   - Basic spectral filtering to differentiate low/mid/high frequency strikes.
   - Adjustable sensitivity per track.

3. **Track System**
   - Up to **12 tracks**.
   - Each track can load one audio sample (WAV, AIFF, MP3).
   - Track-specific controls:
     - Volume
     - Pan
     - Sensitivity threshold
     - Assigned frequency/string range for trigger

4. **Playback & Layering**
   - Play sounds directly in real-time as guitar hits are detected.
   - Ability to record multiple layers (overdub) per track.

5. **Project Saving**
   - Save to `.gpsproj` (JSON-based) containing:
     - Audio sample paths
     - Track settings
     - Recorded sequence data
   - Load previous projects with all settings restored.

6. **UI**
   - Simple Mac-native interface using SwiftUI.
   - Waveform display for each track.
   - Sensitivity sliders, sample browser, and mute/solo buttons.

---

## Technical Stack

- **Language**: Swift 5.x
- **Frameworks**:
  - Core Audio / AVAudioEngine (low-latency I/O and audio processing)
  - SwiftUI (UI layout)
  - Combine (reactive updates for UI controls)
- **Audio Processing**:
  - Real-time transient detection algorithm
  - Simple high/low bandpass filters for frequency-based mapping
- **File Handling**:
  - Codable structs for JSON save/load

---

## Development Roadmap

**Phase 1 (MVP)**
- [ ] Implement Core Audio input/output
- [ ] Implement basic transient detection
- [ ] Trigger sample playback from guitar hits
- [ ] Support loading up to 12 samples
- [ ] Simple SwiftUI track controls
- [ ] Save/load project data

**Phase 2**
- [ ] Add per-track EQ filtering for better hit isolation
- [ ] Velocity sensitivity based on pick attack
- [ ] Metronome & quantization options
- [ ] Export final mix as WAV/MP3

**Phase 3**
- [ ] Advanced spectral analysis to distinguish different guitar hit types
- [ ] Per-track effects (reverb, delay, compression)
- [ ] MIDI export for DAW integration
- [ ] Multi-interface input selection

---

## Installation & Build
1. Clone this repository.
2. Open `GuitarPercussionStudio.xcodeproj` in Xcode.
3. Select a signing team (for running locally).
4. Build and run on macOS 12 or later.

---

## License
MIT License
