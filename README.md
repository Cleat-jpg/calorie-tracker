# Calorie tracker

A small installable web app (PWA) for tracking calories by day and by meal.

- Pick a food, enter grams or kg, see the calories
- Group foods into meals (Meal 1, Meal 2, ...) and rename them
- Calendar picker: every day is saved separately, with a recent-days list
- Meal reminders: in-app notifications while the app is open, plus a daily-repeating
  `.ics` calendar export so your phone alerts you even when the app is closed
- Works offline and installs to the home screen
- Data is stored in your browser (localStorage) on your device. No server, no account.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app (HTML, CSS, JS) |
| `manifest.webmanifest` | Install metadata (name, icons, colors) |
| `sw.js` | Service worker: offline cache and notification taps |
| `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` | App icons |

## Host it free on GitHub Pages

1. Create a new GitHub repository and upload all the files in this folder to the root.
2. Go to **Settings > Pages**. Under **Build and deployment**, choose **Deploy from a branch**,
   pick `main` and `/ (root)`, then save.
3. After a minute your app is live at `https://YOUR-USERNAME.github.io/YOUR-REPO/`.

Pages serves over HTTPS, which installing and notifications both require.

## Install on your phone

- **Android (Chrome):** open the link, tap **Install app** (or the browser menu > **Install app**).
  It installs as a standalone app with its own icon.
- **iPhone (Safari):** open the link, tap Share > **Add to Home Screen**. iOS has no other
  install route for web apps. Notifications on iOS only work for apps added to the Home Screen
  (iOS 16.4 or later).

## About reminders

Web apps cannot run timers in the background, so the in-app notification only fires while the
app is open. For an alarm that always rings, tap **Add to phone calendar** in the app and open the
downloaded `.ics` file: each reminder becomes a daily repeating event with an alert.

## Updating the food list

Edit the `FOODS` array near the top of the script in `index.html`. Each entry is
`["Name", kcal per 100 g]`. After changing files, bump `CACHE` in `sw.js` (for example to
`calorie-tracker-v2`) so installed copies refresh.

Nutrition values are averages from standard tables and are approximate.
