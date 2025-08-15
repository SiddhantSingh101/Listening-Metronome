# 🎵 TempoCoach – Metronome Accuracy & Rhythm Training App

## 📌 Overview

TempoCoach is an **interactive rhythm training app** that goes beyond a traditional metronome. Instead of just giving a click, it **listens to your playing** (guitar, piano, drums, etc.) through your phone’s microphone, analyzes your timing, and provides **real-time feedback** on how well you’re staying in tempo.

The goal is simple:  
👉 Help musicians **develop a rock-solid sense of timing** by showing them where they rush or drag, with **visual feedback, graphs, and coaching tips**.

---

## ✨ Key Features

### Built-in Metronome

- Adjustable tempo (BPM), time signatures (4/4, 3/4, etc.)
- Visual + audible click

### Microphone Input Analysis

- Detects notes, strums, or hits using onset detection (aubio / custom DSP)
- Compares them against the metronome beat grid

### Accuracy Visualization

- Displays a **graph of beats vs. player hits**
- Shows whether you’re **ahead, behind, or right on time**
- Optionally provides **percentage accuracy score**

### Simple Coaching Tips (MVP)

Feedback like:

- _“You tend to rush on downbeats, try relaxing.”_
- _“Great consistency! Keep it up.”_
- _“Dragging on upbeats—focus on subdivision.”_

### Progress Tracking (future)

- Save practice sessions
- Track improvement over time

---

## 🛠 Tech Stack

### Frontend (UI)

- **Kotlin (Android app)** – clean, native UI
- Compose for UI rendering (planned)
- Graphs with MPAndroidChart

### Audio Engine (Core)

- **Aubio** (C library wrapped for Android/Kotlin) for onset detection
- Alternative: **TarsosDSP** (Java-based, easier integration)
- Real-time mic input via Android AudioRecord

### Backend (Optional, Future)

- Could integrate Firebase or Supabase for user profiles & progress storage
- Initial MVP will be offline-only

---

## 🎯 Vision

Most musicians hate practicing with a metronome because it feels unnatural and unforgiving. TempoCoach aims to make the metronome **a coach, not a critic**:

- Natural and supportive, not robotic.
- Focused on **real improvement**, not just a flashing click.
- Helpful for **guitarists, pianists, drummers, and all rhythm-based players**.

---

## 🖼 Example Flow

1. User sets tempo → e.g., **60 BPM, 4/4**
2. App plays clicks → user strums guitar along
3. Mic picks up audio → onset detection identifies strum timing
4. App compares strums vs. metronome grid
5. Graph shows:
   - ✅ Perfectly aligned hits
   - 🔴 Early hits
   - 🔵 Late hits
6. User gets quick coaching feedback

---

## 🚀 Roadmap

### MVP

- Basic metronome
- Audio input + onset detection
- Accuracy graph (metronome vs. player hits)
- Simple feedback messages

### V2

- More detailed coaching tips
- Custom practice modes (e.g., subdivisions, swing feel)
- User stats (accuracy % trend, session history)

### V3

- Cloud sync with Firebase
- Leaderboards & gamification
- Community practice challenges

---

## 🤔 Why This Matters

- Practicing with a metronome builds **rhythmic discipline**, but most musicians avoid it because it feels dry.
- This app makes metronome practice **engaging, visual, and helpful**.
- It’s like having a **personal rhythm coach** in your pocket.

---

## 📌 Status

Currently in **concept + early prototyping**.  
First milestone: **Detect notes from mic input and align them against a 60 BPM click track in 4/4**.

---
