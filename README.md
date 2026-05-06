# Reccurly 📱

A clean, minimal mobile app to track and manage your subscriptions, built with React Native, Expo, and NativeWind.

---

## Features

- **Add & delete subscriptions** — manually add any service with name, price, billing cycle, and category
- **Cost overview** — see your total monthly and yearly spending at a glance
- **Upcoming renewals** — highlights subscriptions renewing within the next 7 days
- **User authentication** — sign in / sign up via Clerk
- **Analytics** — user interactions tracked with PostHog (subscription created, expanded, collapsed, sign-out)

---

## Tech Stack

| | |
|---|---|
| Framework | React Native + Expo |
| Language | TypeScript |
| Styling | NativeWind (Tailwind CSS for React Native) |
| Routing | Expo Router (file-based) |
| Auth | Clerk |
| Analytics | PostHog |
| State | Zustand |
| Date handling | Day.js |

---

## Analytics Events (PostHog)

| Event | Description |
|---|---|
| `subscription_created` | Fired when a new subscription is added |
| `subscription_expanded` | Fired when a subscription card is opened |
| `subscription_collapsed` | Fired when a subscription card is closed |
| `user_signed_out` | Fired on sign-out, followed by `posthog.reset()` |

---

## Getting Started

### Prerequisites

- Node.js 18+
- Expo CLI
- iOS Simulator, Android Emulator, or Expo Go

### Installation

```bash
git clone https://github.com/LuntNicolas/reccurly.git
cd reccurly
npm install
```

### Environment Variables

Create a `.env` file in the root:

```env
EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_key
EXPO_PUBLIC_POSTHOG_API_KEY=your_posthog_key
```

### Run the app

```bash
npx expo start
```

Then open in:
- **Expo Go** — scan the QR code with your phone
- **iOS Simulator** — press `i`
- **Android Emulator** — press `a`

---

## Project Structure

```
reccurly/
├── app/          # Screens & routing (Expo Router)
├── components/   # Reusable UI components
├── constants/    # Colors, config, static data
├── assets/       # Images & fonts
├── lib/          # Utility functions & Zustand store
└── global.css    # NativeWind global styles
```

---

## Status

Work in progress — frontend only. No backend integration yet.
