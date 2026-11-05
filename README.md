# For Esthefanni — A Birthday Story

A private, mobile-first birthday experience made for Esthefanni Carla by Rakesh. Built with React, Vite, Framer Motion, GSAP and React Three Fiber. Personal photographs are stored locally in `src/assets/images` and are not uploaded to a third-party service by the app.

## Run locally

Requirements: Node.js 20.19+ (or 22.12+) and npm.

```bash
npm install
npm run dev
```

Open the local URL printed by Vite (usually http://localhost:5173).

## Production build

```bash
npm run build
npm run preview
```

The production output is written to `dist/` and can be deployed to Vercel as a standard Vite project. No server, API key, analytics, or backend is required.

## Personalize the experience

All content is centralized in `src/config/siteConfig.js`:

- `girlfriendName`, `birthdayDate`, `pin`, and `senderName`
- `heroMessage` and `letter`
- `photos` (hero, lock screen, timeline, gallery, letter, finale)
- `memories`, `appreciations`, and `quiz`
- `music.audioFile`, `music.trackTitle`, `music.artistName`, and `music.coverPhoto`
- `voiceMessage` (reserved for a future local voice-note player)

The current five supplied photos have been converted to optimized WebP copies and saved in `src/assets/images/`. Replace a photo by replacing its import or file in `siteConfig.js`. Keep face framing in mind; CSS uses `object-fit: cover` and per-section object positioning.

### Add music

1. Copy an audio file (for example `birthday-song.mp3`) into `src/assets/audio/`.
2. Import it at the top of `siteConfig.js`, e.g. `import birthdaySong from '../assets/audio/birthday-song.mp3'`.
3. Set `music.audioFile: birthdaySong`, and update the title/artist. Audio never starts automatically; the visitor must press play.

### Secret PIN

Change `pin` in `siteConfig.js`. The PIN is a client-side surprise gate only, not secure authentication. Do not use it to protect sensitive information.

### Dates and message

The birthday is set to November 5, 2026, based on the supplied brief. Update `birthdayDate` if you want another year. The birthday date is currently presented as an editorial date marker; no countdown is shown because the brief's birthday is today.

## Features

- PIN gate with keypad, wrong-code feedback, and unlock transition
- Cinematic intro and full-screen hero
- Scroll-revealed memory timeline and responsive photo gallery with lightbox
- Appreciation stories, interactive memory quiz, canvas scratch card, and gift reveal
- Openable letter, opt-in audio player shell, interactive Three.js cake, final photo reveal, replay, and hidden five-tap star Easter egg
- Reduced-motion support, semantic controls, keyboard-operable gallery and letter, local photo assets, and `noindex,nofollow`

## Notes

- The voice-message section is intentionally omitted until a local voice recording is supplied.
- The music player displays its setup state until a local audio file is configured.
- The cake uses React Three Fiber with a lightweight fallback loading state. If a device/browser cannot run WebGL, the rest of the experience remains usable.
- The envelope contains the full birthday letter and can be opened/closed by click or keyboard.
- The surprise PIN is visible only as masked dots; the actual value is kept in configuration and is not rendered as page text.

## Deploy to Vercel

Import the project repository in Vercel. Framework preset: **Vite**. Build command: `npm run build`. Output directory: `dist`. No environment variables are needed.
