# 🎸 TempoCoach – Guitar Audio Engine

## 📌 Overview
This module is the **heart of TempoCoach**. It listens to a guitar through the device microphone, detects the timing of each strum or note, and compares it against the metronome grid to calculate **accuracy**.  

The goal is to provide **real-time feedback** to help musicians stay in tempo and improve rhythmic precision.

---

## ✨ Key Features

### Real-Time Audio Input
- Capture audio from the phone microphone using **Android AudioRecord**.
- Sample rate: 44.1 kHz (or 48 kHz if necessary for better resolution).  
- Mono channel for simplicity.  

### Preprocessing
- Normalize audio volume to reduce variations between soft and loud playing.
- Optional **band-pass filter** (~80–1200 Hz) to isolate guitar frequencies and reduce background noise.

### Onset Detection
- Detect the exact moment of each strum or note attack.
- Use **Aubio** or **TarsosDSP** libraries for accurate onset detection.
- Onset detection methods:
  - **Energy-based**: detects sudden spikes in amplitude.
  - **Spectral flux / complex domain**: detects changes in spectral content for more robust detection.
- Output: timestamps of detected onsets (in milliseconds).

### Beat Matching
- Compare detected onsets to the **metronome beat timestamps**.
- Calculate **deviation per beat**:
  ```text
  deviation_ms = detected_strum_time - expected_metronome_time
  ```
- Store deviations to generate accuracy statistics.

### Accuracy Visualization
- Provide structured data for the frontend:
  ```json
  [
    {"beat": 1, "offset_ms": -40},
    {"beat": 2, "offset_ms": 15},
    {"beat": 3, "offset_ms": -5}
  ]
  ```
- Can be used to plot graphs showing early/late notes.

### Coaching Tips (MVP)
- Analyze deviation data over time to provide feedback:
  - Early consistently → "You are rushing, relax your strumming."
  - Late consistently → "You are dragging, push slightly ahead of the click."
  - High variance → "Timing is unstable, try slow practice."

---

## 🛠 Tech Stack

- **Language:** Kotlin
- **Audio Libraries:**
  - **Aubio** (C library, Android wrapper)
  - **TarsosDSP** (Java-based alternative)
- **Android Audio API:** AudioRecord for live input
- **Data Output:** JSON objects for frontend consumption

---

## 🖼 Audio Engine Flow

1. **User taps "Start Practice"**
2. AudioRecord begins capturing mic input
3. **Preprocessing**
   - Normalize volume
   - Apply optional band-pass filter
4. **Onset Detection**
   - Detect strum/note attacks in real time
   - Generate timestamps
5. **Beat Comparison**
   - Calculate deviation from metronome grid
6. **Output**
   - Provide deviations to UI
   - Trigger coaching tips if thresholds are exceeded
7. **Frontend**
   - Graph displays accuracy
   - Feedback messages are shown to the user

---

## 🎯 Goals & Limitations

- **Goal:** Accurate detection of guitar timing to provide visual and coaching feedback.
- **Limitations:**
  - Works best on **percussive, distinct strums**.
  - **Soft strumming**, background noise, or overlapping instruments may reduce accuracy.
  - Singing / voice input is possible but less reliable; focus on guitar first.

---

## 🚀 Roadmap for Engine

### MVP
- AudioRecord input
- Onset detection (Aubio/TarsosDSP)
- Beat matching & deviation calculation
- Simple feedback rules

### V2
- Graphical deviation output for UI
- Optional filtering to reduce false positives
- Configurable thresholds for personalized practice

### V3
- Multi-instrument support (piano, bass)
- Voice/singing detection (stretch goal)
- Trend analysis and progress tracking