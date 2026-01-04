# Neon Scavengers: Multiplayer Physics Engine

**Live Demo:** [https://neonscavengers.netlify.app/](https://neonscavengers.netlify.app/)

## Overview
Neon Scavengers is a real-time multiplayer browser game built entirely in **Vanilla JavaScript**.

Unlike standard .io games that rely on heavy frameworks, this project runs on a custom-built physics and networking engine designed to handle high-latency environments (200ms+ RTT). The core engineering challenge was implementing **authoritative server architecture** with **client-side prediction** to ensure responsive movement despite network lag.

## Technical Highlights

### 1. Lag Compensation & Reconciliation
The engine implements "Server Reconciliation" to handle state disagreement between the client and the authoritative server (Firebase).
* **Client-Side Prediction:** Inputs are applied instantly to the local entity for zero-latency feedback.
* **Reconciliation Loop:** When the server returns an authoritative state from the past, the client re-simulates all unacknowledged inputs to correct the current state without "snapping" the player.
* **Code Location:** See `src/engine/network.js` (or your specific file path).

### 2. Custom Physics System
A lightweight 2D AABB (Axis-Aligned Bounding Box) physics engine written from scratch.
* Decoupled rendering loop (p5.js) from the physics tick (60hz fixed).
* Optimized spatial hashing for collision detection.

## Architecture
* **Frontend:** Vanilla JS, p5.js (Rendering only)
* **Backend:** Google Firebase (Realtime Database, Auth)
* **Hosting:** Netlify

## Setup
1. Clone the repo.
2. Open `index.html` in your browser.
