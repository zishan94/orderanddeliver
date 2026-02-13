# 💊 Order & Deliver

A premium delivery app built with Expo React Native — featuring real-time tracking, OpenStreetMap maps, and a luxury UI.

## Features

- **3 User Roles:** Consumer, Approver, Driver
- **Phone auth** (demo mode — any 6-digit code works)
- **Staff login** (username + password for approvers & drivers)
- **17 products** across 6 categories (Classic, Fruity, Mint, Sweet, Mix, Premium)
- **Real-time** order updates, driver tracking, and chat via WebSocket
- **OpenStreetMap** with Leaflet — fully open source, no Google
- **OSRM routing** for delivery ETAs
- **Luxury light theme** — clean whites, subtle shadows, elegant typography
- **Splash animation** with brand identity
- **TypeScript** throughout

## Screenshots

💊 Luxury light design with warm off-whites, white cards, dark navy accents, and subtle shadows.

## Quick Start

### 1. Install dependencies

```bash
npm install
cd server && npm install && cd ..
```

### 2. Start the backend

```bash
cd server
npx tsx index.ts
```

Server runs on `http://localhost:3001`. SQLite DB auto-creates with 17 products and demo staff accounts.

### 3. Start the Expo app

```bash
npx expo start
```

Scan the QR code with Expo Go (Android) or press `w` for web.

### 4. Demo Accounts

**Consumer:** Enter any phone number → any 6-digit code → start browsing

**Staff:**
| Role | Username | Password |
|------|----------|----------|
| Approver | `approver1` | `admin123` |
| Driver | `driver1` | `driver123` |
| Driver | `driver2` | `driver123` |

## Architecture

```
orderanddeliver/
├── app/                  # Expo Router screens
│   ├── (auth)/          # Landing, phone login, staff login
│   ├── consumer/        # Browse, order, track, orders, profile
│   ├── approver/        # Dashboard, active orders, chat, profile
│   └── driver/          # Deliveries, route, profile
├── components/          # MapView (Leaflet), OrderCard, ChatView, etc.
├── contexts/            # Auth, Socket, Location providers
├── constants/           # Theme (luxury light), config
└── server/              # Express + Socket.io + SQLite
    ├── index.ts         # Server entry
    ├── db.ts            # Database + seed data (17 products)
    └── routes/          # REST API endpoints
```

## Product Categories

| Category | Products | Price Range |
|----------|----------|-------------|
| 🍎 Classic | Al Fakher Double Apple, Grape, Adalya Two Apples | CHF 0.08-0.09/g |
| 🍓 Fruity | Adalya Love 66, Lady Killer, Holster Ice Kaktus, Fumari Tangelo | CHF 0.09-0.11/g |
| 🌿 Mint | Tangiers Cane Mint, Al Fakher Mint | CHF 0.07-0.12/g |
| 🍬 Sweet | Fumari White Gummy Bear, Blueberry Muffin | CHF 0.11/g |
| 🍹 Mix | Starbuzz Blue Mist, Pirates Cave, Al Fakher Watermelon Mint | CHF 0.08-0.12/g |
| ⭐ Premium | Darkside Supernova, Deep Dive, Tangiers Kashmir Peach | CHF 0.13-0.14/g |

## API Endpoints

| Method | Path | Description |
|--------|------|-------------|
| POST | `/api/auth/request-code` | Request SMS code (demo) |
| POST | `/api/auth/verify` | Verify code + login |
| POST | `/api/auth/staff-login` | Staff username/password login |
| GET | `/api/products` | List all products |
| POST | `/api/orders` | Place an order |
| GET | `/api/orders/pending` | Pending orders (approver) |
| GET | `/api/orders/active` | Active orders |
| POST | `/api/orders/:id/approve` | Approve order |
| POST | `/api/orders/:id/reject` | Reject order |
| POST | `/api/orders/:id/assign` | Assign driver |
| POST | `/api/orders/:id/delivering` | Start delivery |
| POST | `/api/orders/:id/delivered` | Complete delivery |
| GET/POST | `/api/messages` | Chat messages |

## Tech Stack

- **Frontend:** Expo SDK 54, React Native, TypeScript, Expo Router
- **Backend:** Express.js, Socket.io, better-sqlite3
- **Maps:** Leaflet + OpenStreetMap (fully open source)
- **Routing:** OSRM (router.project-osrm.org)
- **UI:** Luxury light theme, react-native-reanimated, expo-linear-gradient

## License

MIT
