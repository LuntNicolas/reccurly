<wizard-report>
# PostHog post-wizard report

The wizard has completed a deep integration of PostHog analytics into the Recurrly Expo app. The following changes were made:

- **`app.config.js`** (new): Expo config that exposes `POSTHOG_PROJECT_TOKEN` and `POSTHOG_HOST` environment variables to the app via `expo-constants` extras.
- **`src/config/posthog.ts`** (new): PostHog client singleton initialized with the token and host from `expo-constants`, with batching, lifecycle events, and debug logging configured.
- **`app/_layout.tsx`**: Wrapped the app in `PostHogProvider`, added manual screen tracking using `usePathname` + `useGlobalSearchParams` with a `useEffect` that calls `posthog.screen()` on every route change.
- **`app/(auth)/sign-in.tsx`**: Added import for the `posthog` instance. The file already had `posthog.capture('user_signed_in')`, `posthog.capture('user_sign_in_failed')`, and `posthog.identify()` calls — these now resolve correctly.
- **`app/(tabs)/index.tsx`**: Added `usePostHog()` hook and a `handleSubscriptionPress` handler that fires `subscription_expanded` when a subscription card is opened.
- **`app/subscriptions/[id].tsx`**: Added `usePostHog()` hook and a `useEffect` that fires `subscription_viewed` when the detail screen mounts.
- **`.env`**: `POSTHOG_PROJECT_TOKEN` and `POSTHOG_HOST` written (covered by `.gitignore`).
- **`posthog-react-native`** and **`react-native-svg`** installed via `npx expo install`.

| Event | Description | File |
|---|---|---|
| `user_signed_in` | User successfully signed in with email and password | `app/(auth)/sign-in.tsx` |
| `user_sign_in_failed` | User attempted to sign in but received an error | `app/(auth)/sign-in.tsx` |
| `subscription_expanded` | User expanded a subscription card on the home screen | `app/(tabs)/index.tsx` |
| `subscription_viewed` | User navigated to the subscription detail page | `app/subscriptions/[id].tsx` |

User identification (`posthog.identify`) is called on successful sign-in with the user's email address.

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behavior, based on the events we just instrumented:

- **Dashboard – Analytics basics**: https://us.posthog.com/project/365303/dashboard/1420352
- **Sign-in to Subscription Engagement Funnel**: https://us.posthog.com/project/365303/insights/7vFInjA6
- **Sign-in Success vs Failure**: https://us.posthog.com/project/365303/insights/tYqCVO7r
- **Subscription Engagement**: https://us.posthog.com/project/365303/insights/tmOpjuQc
- **Daily Active Users**: https://us.posthog.com/project/365303/insights/QkdASBea
- **Sign-in Failure Rate**: https://us.posthog.com/project/365303/insights/u2GEsX96

### Agent skill

We've left an agent skill folder in your project. You can use this context for further agent development when using Claude Code. This will help ensure the model provides the most up-to-date approaches for integrating PostHog.

</wizard-report>
