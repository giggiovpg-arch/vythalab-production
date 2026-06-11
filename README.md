# Vytha Lab

Vytha Lab is a Flutter health, training, nutrition, habit, and longevity app.
The app combines FlutterFlow-generated foundations with custom Dart services,
local persistence, local notifications, AI-assisted coaching flows, and AdMob
placements.

Last updated: 2026-06-11

## Contents

- [Current Features](#current-features)
- [Architecture](#architecture)
- [Data and Persistence](#data-and-persistence)
- [Notifications](#notifications)
- [Ads](#ads)
- [AI Services](#ai-services)
- [Project Layout](#project-layout)
- [Run and Verify](#run-and-verify)
- [Privacy and Release Notes](#privacy-and-release-notes)
- [License](#license)

## Current Features

### Home and Daily Flow

- `DashboardHojeWidget` is the main daily dashboard.
- Shows the VythaLab header, greeting, consistency/readiness style summaries,
  nutrition progress, quick actions, and the daily checklist.
- The daily checklist includes normal daily items plus scheduled tasks from
  `Calendario` when the current weekday matches the task day.
- Scheduled checklist items can create local reminders for that exact weekly
  task.

### Calendario

- Dedicated `CalendarioWidget` page in the bottom menu.
- Replaces the old "Minha Semana" block that previously lived inside Treino.
- Supports multiple tasks per weekday.
- Task types currently include workout routines, yoga sessions, corrida, and
  descanso.
- Weekly tasks persist across page changes and app restarts through
  `WeeklyScheduleService`.
- The same weekly data feeds both the Calendario planning UI and the Home
  checklist for the matching weekday.

### Treino and Performance

- Workout dashboard: `WorkoutTrackerWidget`.
- Active workout tracking: `ActiveWorkoutWidget`.
- Exercise library: `ExerciseLibraryWidget`.
- Routine creation and editing: `RoutineBuilderWidget`.
- AI routine creation: `AiRoutineCreatorWidget`.
- Performance overview: `PerformanceHubWidget`.
- Workout state is backed by SQLite models/repositories under
  `lib/backend/sqlite/`.

### Yoga and Mobility

- Yoga dashboard: `YogaWidget`.
- Session library and session details.
- Active timed yoga session flow.
- Pose library.
- AI yoga flow generator.

### Corrida

- Running dashboard: `RunningDashboardScreen`.
- Active run tracking: `ActiveRunScreen`.
- Run history and run detail screens.
- Route preview components.
- Local running repository and tracker service live under `lib/services/`.

### Nutrition and Macros

- AI macro tracker: `AIMacroTrackerWidget`.
- AI meal planner: `AIMealPlannerWidget`.
- Macro goals, macro logs, meal plan entries, and daily nutrition totals are
  stored in `VythaAppState`.
- Fitness tool calculators can save derived macro targets through
  `FitnessToolsRepository`.

### Ferramentas

- Tool hub: `FerramentasWidget`.
- TDEE calculator.
- Macro calculator.
- Readiness score.
- Cutting/bulking calculator.
- AI diet analysis.
- AI workout generator.

### Longevidade

- Biological age screen.
- Longevity dashboard.
- Resilience score card.
- Longevity cards are free features in the current build.

### Habits and Local Reminders

- Habit dashboard, habit templates, habit create/edit flow, and weekly habit
  report live under `lib/pages/local_notifications_habits/`.
- Habit data is managed by `HabitState` and SQLite habit storage.
- Habit reminders use local notifications only.

### Biometrics, Profile, and Onboarding

- Biometrics dashboard with recovery, sleep, chart, and metric widgets.
- Evolution/progress page for body and progress tracking.
- User profile data and privacy/export controls.
- Onboarding flow: `OnboardingGlitchIntroWidget`.
- Pedometer support is provided by `PedometerService`.

## Architecture

The app is a Flutter application with a FlutterFlow base and custom feature
modules layered on top.

### App Entry Point

- `lib/main.dart` initializes Flutter, Mobile Ads, FlutterFlow theme state,
  global app state, habits, weekly task reminders, and providers.
- `MaterialApp.router` uses the FlutterFlow/GoRouter navigation setup.
- The app shell wraps screens in the custom VythaLab header and
  `WavyBackground`.

### State Management

- `provider` is the main state-management layer.
- `VythaAppState` holds profile, onboarding, privacy settings, macro logs,
  meal plan entries, saved macro targets, daily checks, and app-level totals.
- `HabitState` manages habit records and reminder state.
- `WorkoutActiveState` manages active workout state.
- `PedometerService` and `RunningTrackerService` are registered as
  `ChangeNotifier` services.
- `WeeklyScheduleService.changes` is a `ValueNotifier` used to refresh pages
  that depend on the weekly plan.

### Routing

Routes are registered in `lib/flutter_flow/nav/nav.dart` and exported through
`lib/index.dart`. Important route groups include:

- Home: `DashboardHojeWidget`.
- Nutrition: AI meal planner and AI macro tracker.
- Training: workout tracker, exercise library, routine builder, active workout.
- Calendar: `CalendarioWidget`.
- Tools: Ferramentas and calculator/detail screens.
- Habits: dashboard, templates, reports, create/edit.
- Health: biometrics, evolution, biological age/longevity.
- Yoga: dashboard, sessions, active session, poses, AI flow.
- Running: dashboard, active run, history, detail.

### UI Layer

- Reusable widgets live in `lib/components/`.
- Feature screens live in `lib/pages/`.
- FlutterFlow utilities, theme, icons, forms, and generated navigation helpers
  live in `lib/flutter_flow/`.
- Shared visual surfaces include `WavyBackground`,
  `VythaVioletSurface`, metric cards, daily check rows, ad widgets, and bottom
  navigation.

## Data and Persistence

The app is local-first. Most user data is stored on the device.

- `SharedPreferences`:
  - `VythaAppState` JSON snapshot.
  - Weekly schedule tasks and task reminders.
  - Some feature settings and cached local values.
- SQLite via `sqflite`:
  - Workout models and workout history.
  - Habit models, completions, and reminder metadata.
- Running:
  - `RunningLocalRepository` stores local running sessions.
  - `RunningTrackerService` manages active run state.
- Fitness tools:
  - Calculator results and saved macro targets are handled by
    `FitnessToolsRepository`.
- Longevity:
  - Longevity calculations and storage are split between
    `LongevityEngine`, `LongevityRepository`, and `LongevityAiService`.

## Notifications

Notifications are local device notifications, not remote push.

- Main service: `lib/services/notification_service.dart`.
- Packages: `flutter_local_notifications`, `timezone`, and
  `flutter_timezone`.
- Habit reminders are scheduled locally.
- Calendar task reminders are scheduled weekly for a specific weekday and time.
- On startup, `WeeklyScheduleService.rescheduleActiveTaskReminders()` restores
  active calendar reminders.
- Android uses notification, boot, exact-alarm, and scheduled-notification
  receivers required by `flutter_local_notifications`.
- iOS uses local notification permission prompts from
  `flutter_local_notifications`.

## Ads

AdMob support is initialized through `initializeMobileAds()` in `main.dart`.

- Ad placement policy lives in `lib/services/ad_policy_service.dart`.
- Ad unit selection lives in `lib/services/admob_ad_unit_ids.dart`.
- Debug and profile builds always use Google test ad unit IDs.
- Release builds use configured Android IDs when present and fall back to test
  IDs when an ID is missing.
- Android app ID is injected from `android/local.properties` with a safe test
  fallback in Gradle.
- iOS ad unit IDs are currently unset and should be configured before an iOS
  ad-enabled release.
- `AdPlaceholderWidget` currently loads real banner/native ad widgets for
  supported inline placements and uses fallback UI while loading or on error.

## AI Services

AI-assisted features are routed through service classes rather than directly
from widgets.

- `DeepseekApiService` supports macro, meal, diet, workout, and related AI
  flows.
- `RunningAiAnalysisService` supports running analysis.
- `LongevityAiService` supports longevity-oriented AI output.
- AI features should avoid sending unnecessary identifiers or unrelated health
  data.

## Project Layout

```text
vytha_lab/
|-- android/                       # Android native project and Gradle config
|-- ios/                           # iOS native project
|-- assets/                        # Fonts, images, videos, audio, PDFs
|-- lib/
|   |-- app_state.dart             # Global app state and macro/profile data
|   |-- backend/sqlite/            # SQLite models, DB access, active workout/habits
|   |-- components/                # Reusable UI widgets and shared surfaces
|   |-- flutter_flow/              # FlutterFlow theme, utilities, routing helpers
|   |-- models/                    # Feature models and DTOs
|   |-- pages/                     # Feature screens
|   |   |-- biological_age/
|   |   |-- calendario/
|   |   |-- corrida/
|   |   |-- ferramentas/
|   |   |-- local_notifications_habits/
|   |   |-- workout_tracker/
|   |   `-- yoga/
|   |-- services/                  # Business logic, ads, AI, notifications, repositories
|   `-- main.dart                  # App bootstrap
|-- test/                          # Flutter tests
|-- PRIVACY.md                     # Current privacy policy draft
`-- pubspec.yaml                   # Dependencies, assets, package metadata
```

## Run and Verify

Install dependencies:

```bash
flutter pub get
```

Run the app:

```bash
flutter run
```

Analyze:

```bash
flutter analyze
```

Run tests:

```bash
flutter test
```

Build a debug APK:

```bash
flutter build apk --debug
```

## Privacy and Release Notes

- The current privacy policy draft is in `PRIVACY.md`.
- Keep `PRIVACY.md`, app-store disclosures, permission prompts, AdMob usage,
  AI data flow, and actual app behavior aligned before release.
- The app is a wellness and fitness tool. It is not a medical device and should
  not be described as providing diagnosis, treatment, or emergency care.
- Before publishing, verify production AdMob IDs, iOS AdMob configuration,
  notification permissions, location/activity permissions, AI provider
  disclosures, and any account/data deletion requirements.

## License

This project is configured as a private package with `publish_to: 'none'`.
