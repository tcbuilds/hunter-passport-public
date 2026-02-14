<p align="center">
  <img src="assets/logo.png" alt="Hunter Passport" width="140" />
</p>

<h1 align="center">Hunter Passport</h1>

<p align="center">
  <strong>All your hunting & fishing licenses. One app. Works offline.</strong>
</p>

<p align="center">
  <a href="https://hunterpassport.com">Website</a>&nbsp;&nbsp;&bull;&nbsp;&nbsp;<a href="https://app.hunterpassport.com">Web App</a>&nbsp;&nbsp;&bull;&nbsp;&nbsp;<a href="https://play.google.com/store/apps/details?id=com.hunterpassport.app">Google Play</a>
</p>

<br />

## The Problem

Hunters and anglers who hold licenses across multiple states carry a mess of paper cards, PDFs, and screenshots. When a game warden asks for proof of license — often miles from cell service — digging through that mess is stressful and slow.

## The Solution

Hunter Passport consolidates every license into a single offline-first wallet. Snap a photo, the app extracts the fields automatically, and your license is stored locally on-device. No network required to view it — ever.

**One tap. Three seconds. Done.**

<br />

<p align="center">
  <img src="assets/wallet-home.jpg" alt="Wallet — licenses organized by state" width="270" />&nbsp;&nbsp;&nbsp;
  <img src="assets/scan-license.jpg" alt="Scan a license with camera or gallery" width="270" />&nbsp;&nbsp;&nbsp;
  <img src="assets/ocr-extraction.jpg" alt="AI-powered field extraction with confidence scores" width="270" />
</p>

<p align="center">
  <img src="assets/license-detail.jpg" alt="License detail view with original image" width="270" />&nbsp;&nbsp;&nbsp;
  <img src="assets/quick-display.jpg" alt="Quick Display — high contrast, warden-ready" width="270" />&nbsp;&nbsp;&nbsp;
  <img src="assets/cloud-sync.jpg" alt="Cloud sync and subscription management" width="270" />
</p>

<br />

## Features

- **Offline-first wallet** — All data lives on-device in SQLite. No internet needed to view licenses.
- **AI-powered OCR** — Snap a photo of any license. On-device ML Kit + Gemini Flash extracts every field with confidence scores. Edit anything it misses.
- **Quick Display** — One-tap high-contrast mode designed for showing a game warden in the field. Large license number, dark background, readable in direct sunlight.
- **Multi-state support** — Organize licenses across all 50 states. Hunting, fishing, combo, permits, tags, stamps, and hunter education cards.
- **Cloud backup** — Optional encrypted sync to the cloud. Switch phones without losing anything.
- **Expiration alerts** — Push notifications 30 days before any license expires.
- **Original image access** — Swipe to view the original license photo at any time.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18, TypeScript, Tailwind CSS |
| Build | Vite |
| Mobile | Capacitor (Android + iOS) |
| State | Zustand + persist middleware |
| Local DB | SQLite (offline source of truth) |
| Auth | Supabase (Google OAuth, magic link, email) |
| Cloud | Supabase PostgreSQL + Storage |
| OCR | ML Kit (on-device) + Gemini Flash (field extraction) |
| Payments | RevenueCat |
| Analytics | GA4 |

## Architecture

```
┌─────────────────────────────────────────────┐
│                  React UI                    │
│          (Tailwind + Capacitor)              │
├─────────────────────────────────────────────┤
│              Zustand Stores                  │
│         (in-memory reactive state)           │
├─────────────────────────────────────────────┤
│          SQLite (source of truth)            │
│       All reads local, writes local-first    │
├──────────────────────┬──────────────────────┤
│   ML Kit (on-device) │  Gemini Flash (API)  │
│   < 500ms OCR        │  field extraction    │
├──────────────────────┴──────────────────────┤
│          Supabase (cloud sync)               │
│    last-write-wins · encrypted · optional    │
└─────────────────────────────────────────────┘
```

## Design Philosophy

**Modern Minimal** — not the camo-and-antlers aesthetic you'd expect. Clean cards, forest green accents, slate neutrals, and typography-forward UI inspired by Stripe and Linear.

The entire UX is filtered through one scenario:

> You're 2 miles into public land with no cell service. A game warden approaches. You open the app, tap your state, hit Quick Display. License number fills the screen in high contrast. **3 seconds.**

Every design decision serves that moment.

## Status

Hunter Passport is live on [Google Play](https://play.google.com/store/apps/details?id=com.hunterpassport.app) and the [web](https://app.hunterpassport.com). iOS coming soon.

## License

This repository contains the public showcase for Hunter Passport. The application source code is proprietary.

Copyright 2025-2026 Hunter Passport. All rights reserved.
