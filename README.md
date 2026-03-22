# ⚡ Pulse — Secure Global Messaging Platform

> A full-featured messaging platform built for privacy, speed, and scale — inspired by Telegram and WhatsApp, redesigned for the modern web.

---

## 📁 Project Files

| File | Description |
|------|-------------|
| `pulse-website.html` | Full marketing website (landing page) |
| `pulse-chat.html` | In-browser chat application UI |
| `README.md` | This file |

---

## 🚀 Overview

Pulse is a secure, worldwide messaging platform with:

- **Phone-number registration** with SMS OTP verification (190+ countries)
- **Unlimited private messaging** — no caps, no throttling
- **Group chats** up to 1,000 members with admin controls
- **Status updates** — share moments with your contacts
- **HD voice & video calls** via WebRTC
- **End-to-end encryption** on every message, call, and file
- **Multi-device support** — iOS, Android, Web, Windows, macOS

---

## 📂 File Breakdown

### `pulse-website.html` — Marketing Website

A single-file marketing website with the following sections:

| Section | Description |
|---------|-------------|
| **Nav** | Fixed sticky navbar with frosted-glass scroll effect, mobile hamburger menu |
| **Hero** | Full-screen hero with animated phone mockup, floating stat cards, App Store / Google Play / Web download badges |
| **Stats Band** | 2.4B messages/day · 190+ countries · 98ms delivery · 256-bit AES |
| **Features Bento** | Asymmetric card grid — DMs, groups, status, file sharing, multi-device, profiles |
| **Security** | Rotating encryption ring animation, Signal Protocol overview, Zero Knowledge architecture |
| **How It Works** | 4-step onboarding flow with staggered reveal animations |
| **Testimonials** | 3-card testimonial section |
| **Pricing** | Free / Pro ($5/mo) / Business ($12/user/mo) |
| **CTA** | Platform download section — iOS, Android, Windows, macOS, Web |
| **Footer** | 4-column footer with legal, social, and brand info |

**Dependencies:** Zero. Pure HTML + CSS + vanilla JS. No frameworks, no build step.

---

### `pulse-chat.html` — Chat Application UI

A fully interactive, single-page chat app prototype:

| Feature | Details |
|---------|---------|
| **Registration flow** | Phone entry → SMS OTP (6-digit) → Profile setup |
| **Sidebar** | Chat list with tabs: All / DMs / Groups / Status |
| **Messaging** | Send/receive messages, emoji picker, simulated auto-replies |
| **Groups** | Create group chats, add members, group info panel |
| **Status feed** | Post status updates, like and reply |
| **Right panel** | Contact/group info, members list, encryption status |
| **Security UI** | E2E encryption badge on every conversation |

**Demo credentials:** Any phone number works. The 6-digit OTP is shown on screen (demo mode).

---

## 🛠 Running Locally

No build tools required. Open either file directly in a browser:

```bash
# macOS / Linux
open pulse-website.html
open pulse-chat.html

# Windows
start pulse-website.html
start pulse-chat.html

# Or use a local server (recommended for full feature support)
npx serve .
# Then visit http://localhost:3000
```

---

## 🔐 Security Architecture (Production Spec)

The UI is built with these production security principles in mind:

### Encryption
- **Signal Protocol** for end-to-end encryption of all messages
- **AES-256-GCM** for data at rest
- **TLS 1.3** for all data in transit
- **Perfect Forward Secrecy** — new keys per session

### Authentication
- Phone number + SMS OTP (primary)
- Optional 2FA via TOTP authenticator app
- Biometric unlock (Face ID / fingerprint) on mobile
- Session management with device-level keys

### Privacy
- Zero-knowledge server architecture — Pulse cannot read your messages
- Minimal metadata collection — we don't log who you message or when
- Disappearing messages — auto-delete after configurable intervals
- No ads, no data selling, ever

---

## 🏗 Production Stack (Recommended)

To build Pulse into a production app, use the following stack:

### Backend
```
Node.js / Bun          — Runtime
Fastify or Hono        — HTTP server
Socket.io or uWebSockets — Real-time WebSocket layer
PostgreSQL             — User accounts, group metadata
Redis                  — Presence, message queues, sessions
S3-compatible storage  — File and media uploads
```

### Frontend
```
React Native           — iOS + Android
Electron               — Windows + macOS desktop
Next.js                — Web app (this prototype → production)
```

### Infrastructure
```
Twilio / AWS SNS       — SMS OTP delivery (190+ countries)
WebRTC (Mediasoup)     — Voice & video calls
Cloudflare             — CDN, DDoS protection, edge routing
Docker + Kubernetes    — Container orchestration
```

### Encryption
```
libsignal-protocol     — E2E encryption (Signal Protocol)
node-forge / WebCrypto — Key generation and management
```

---

## 📱 Phone Registration Flow

```
1. User enters country code + phone number
2. Backend sends OTP via Twilio SMS
3. User enters 6-digit OTP (expires in 10 minutes)
4. Backend verifies OTP, creates account if new
5. User sets up profile (name, photo, username, bio)
6. Encryption keys generated locally on device
7. Public key uploaded to server; private key never leaves device
```

---

## 💬 Messaging Architecture (Production)

```
Client A                    Server                    Client B
   |                           |                          |
   |── Encrypt msg (B's key) ──>|                          |
   |                           |── Forward encrypted ───> |
   |                           |    (server can't read)   |
   |                           |                          |── Decrypt (A's key)
```

Messages are encrypted client-side before transmission. The server acts as a relay only — it never has access to plaintext content.

---

## 🌍 Internationalization

Pulse supports registration from 190+ countries including:

- North America: +1 (US/Canada)
- Europe: +44 (UK), +49 (DE), +33 (FR), +34 (ES), +39 (IT), +31 (NL)
- Asia-Pacific: +91 (IN), +81 (JP), +86 (CN), +82 (KR), +61 (AU), +62 (ID)
- Americas: +55 (BR), +52 (MX)
- Africa/Middle East: +234 (NG), +27 (ZA), +971 (UAE)
- Russia/CIS: +7

All phone numbers are normalized to E.164 format before storage.

---

## 📋 Feature Checklist

### Core (Implemented in UI prototype)
- [x] Phone number registration with country code selector
- [x] SMS OTP verification flow
- [x] User profile creation (name, photo, username, bio)
- [x] Private messaging (DMs)
- [x] Group chat creation and management
- [x] Status updates (post, like, reply)
- [x] Emoji picker
- [x] Read receipts (✓✓)
- [x] Online presence indicators
- [x] Unread message badges
- [x] Contact/group info right panel
- [x] Encryption badges on all conversations
- [x] Simulated auto-replies (demo mode)

### Production (Backend required)
- [ ] Real SMS OTP delivery via Twilio
- [ ] Persistent message storage
- [ ] Real-time WebSocket messaging
- [ ] Signal Protocol E2E encryption
- [ ] Voice calls (WebRTC)
- [ ] Video calls (WebRTC)
- [ ] File and media uploads (S3)
- [ ] Push notifications (FCM / APNs)
- [ ] Disappearing messages
- [ ] Message search
- [ ] Multiple device sync
- [ ] Admin dashboard (Business tier)

---

## 🎨 Design System

| Token | Value |
|-------|-------|
| Primary font | Bebas Neue (display), Instrument Sans (body), Instrument Serif (italic) |
| Background | `#05050a` (ink) |
| Surface | `#1e1e28` |
| Accent | `#5b46ff` (pulse purple) |
| Secondary | `#38f0d4` (cyan) |
| Highlight | `#b8ff57` (lime) |
| Danger | `#ff4d6d` (rose) |
| Border | `rgba(255,255,255,0.08)` |

---

## 📄 License

This project is a UI prototype / demonstration. For production use, ensure compliance with:

- **Telecom regulations** in target markets (SMS OTP, carrier agreements)
- **GDPR** (EU users)
- **CCPA** (California users)
- **End-to-end encryption export laws** (varies by country)
- **App Store / Google Play policies** for messaging apps

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/my-feature`
5. Open a Pull Request

---

## 📬 Contact

Built with ⚡ by the Pulse team.

- Website: [pulse.app](#)
- Twitter/X: [@pulseapp](#)
- Email: hello@pulse.app
- Security disclosures: security@pulse.app

---

*Pulse — Talk freely. Forever.*
