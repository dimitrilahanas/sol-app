# Sol.

A Flutter mobile dashboard for exploring weather on Mars, powered by a custom FastAPI backend.

<p align="center">
<img src="1.png" alt="Sol home screen" width="250"/>
<img src="2.png" alt="Sol weather detail" width="250"/>
</p>

---

## About

Sol. displays Martian weather data in a clean, mobile-friendly interface. Pick a sol (a Martian day) and see its temperature, season and wind conditions at a glance.

The app doesn't call NASA directly. A dedicated Python backend fetches and processes data from NASA's InSight API, which keeps the app lightweight and focused on UI.

---

## Architecture

Sol. is split across two repositories:

| Repo | Role | Stack |
|---|---|---|
| **sol-app** (this repo) | Mobile dashboard | Flutter, Dart |
| [**sol-api**](https://github.com/dimitrilahanas/sol-api) | Fetches, processes and serves the weather data | Python, FastAPI |

```
NASA InSight API  →  sol-api (FastAPI)  →  sol-app (Flutter)
```

---

## Features

- Shows the latest available sol on launch
- Select any sol to view:
  - Average temperature
  - Martian season
  - Wind direction
  - Wind speed
- Light and dark themes
- API-driven: all data comes through the backend

---

## Code Structure

```
lib/
├── models/
│   ├── DataModel      # a single weather metric (temperature, wind speed…)
│   └── SolModel       # all weather data for one sol
├── services/
│   └── HttpServices   # requests to sol-api
├── widgets/
│   ├── HomeScreen     # main dashboard
│   ├── SolHeader      # selected sol number and header
│   ├── SolSelector    # horizontal ChoiceChip list of sols
│   ├── WeatherGrid    # 2×2 grid of metrics
│   └── DataWidget     # individual metric card
└── theme/
    └── DefaultTheme   # light and dark colour schemes
```

---

## Getting Started

1. Clone and run [sol-api](https://github.com/dimitrilahanas/sol-api) first.
2. Clone this repo and install dependencies:
   ```bash
   git clone https://github.com/dimitrilahanas/sol-app.git
   cd sol-app
   flutter pub get
   ```
3. Point `HttpServices` at your running API, then:
   ```bash
   flutter run
   ```

---

## Status

Complete and functional.

**Next up:** refactor for readability and maintainability.

> **Note:** NASA's InSight mission ended in December 2022, so the dataset is historical and covers the sols InSight recorded.
