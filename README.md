# NightSafetyApp

**NightSafetyApp** is an Android application that visualizes multiple walking/driving routes between two points and analyzes the safety of each route using a simple risk calculation model. The app helps users choose the safest path at night based on crime data, lighting, and crowd density.

---

## Features

* Interactive map view powered by **OSMDroid**.
* Display of **three alternative routes**:

  * **Green → SAFE**
  * **Yellow → CAUTION**
  * **Red → UNSAFE**
* Start and destination markers with **clear labels**.
* Route labels display **risk levels mid-route**.
* Risk calculation considers:

  * Crime factor
  * Lighting conditions
  * Crowd presence
* Simulated **AI processing delay** to mimic real-world route safety analysis.

---

## Screenshots

*(Add your screenshots here for better presentation)*

---

## Getting Started

### Prerequisites

* Android Studio (Arctic Fox or newer recommended)
* Android SDK 30+
* Minimum Android API Level 21

---

### Installation

1. Clone the repository:

```bash
git clone https://github.com/yourusername/NightSafetyApp.git
```

2. Open the project in **Android Studio**.
3. Ensure **OSMDroid dependency** is in your `build.gradle`:

```gradle
implementation 'org.osmdroid:osmdroid-android:6.1.15'
```

4. Add your **marker icons** in `res/drawable`:

* `marker_white.xml` → for start/end
* `marker_green.xml` → for safe route
* `marker_yellow.xml` → for caution route
* `marker_red.xml` → for unsafe route

5. Build and run the app on an Android device or emulator.

---

## How It Works

1. The user opens the app and sees a map centered on Bangalore.
2. Click the **search button** to enter a destination.
3. Tap **Analyze Safety** to compute routes.
4. The app draws **three routes** with corresponding colors:

   * **Green**: safe, low risk
   * **Yellow**: caution, moderate risk
   * **Red**: unsafe, high risk
5. The route risk is calculated using segment factors for crime, lighting, and crowd.
6. The mid-route labels display the **risk level**, and start/end markers are clearly distinguished.

---

## Risk Calculation

Risk is determined by:

```text
risk = 0.45 * crime + lighting_factor + crowd_factor
```

* Lighting factor: 0.05 if well-lit, 0.25 if dark
* Crowd factor: 0.03 if people present, 0.10 if isolated

Route risk is aggregated using:

```text
combined = 0.65 * max(segmentRisks) + 0.35 * avg(segmentRisks)
score = combined * 10 (clamped 1–10)
```

Labels are assigned as:

* 1–3 → SAFE
* 4–6 → CAUTION
* 7–10 → UNSAFE

---

## Project Structure

```
NightSafetyApp/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/nightsafetyapp/
│   │   │   │   ├── MainActivity.kt
│   │   │   │   └── RouteResultActivity.kt
│   │   │   ├── res/
│   │   │   │   ├── layout/activity_main.xml
│   │   │   │   ├── layout/activity_route_result.xml
│   │   │   │   ├── drawable/marker_white.xml
│   │   │   │   ├── drawable/marker_green.xml
│   │   │   │   ├── drawable/marker_yellow.xml
│   │   │   │   └── drawable/marker_red.xml
│   │   │   └── AndroidManifest.xml
├── build.gradle
└── README.md
```

---

## License

MIT License © 2026

Do you want me to do that too?
