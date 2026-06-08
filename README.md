# Vytha Lab

Vytha Lab is a comprehensive, multi-platform health and fitness tracking application built with Flutter. It integrates various wellness features including workout tracking, AI-powered meal planning, biometric data monitoring, and daily habit tracking.

## 📚 Menu

*   [Key Features](#key-features)
*   [Technology Stack](#technology-stack)
*   [Project Structure](#project-structure)
*   [Getting Started](#getting-started)
*   [Privacy & Terms](#privacy-and-terms)
    *   [Privacy Policy Draft](#privacy-policy-draft)
    *   [Terms of Use](#terms-of-use)
*   [Utility Scripts](#utility-scripts)
*   [License](#license)

<a id="key-features"></a>

## 🚀 Key Features

*   **Dashboard & Daily Tracking**: A central hub (`dashboard_hoje`) for an overview of daily progress.
*   **Workout & Performance**:
    *   **Workout Tracker**: Track active workouts and view exercise history.
    *   **Routine Builder**: Create custom workout routines.
    *   **Exercise Library**: A database of exercises.
    *   **Performance Hub**: Monitor fitness progression and metrics.
    *   **Yoga**: Specialized tracking for yoga sessions.
*   **Nutrition & Diet**:
    *   **AI Meal Planner**: Generate meal plans utilizing AI.
    *   **AI Macro Tracker**: Track and analyze macronutrient intake.
*   **Health & Biometrics**:
    *   **Biometrics Dashboard**: Track vital health metrics and measurements.
    *   **Evolution Progress**: Visualize physical changes over time.
    *   **Pedometer Integration**: Track daily steps directly via device sensors.
*   **Habit Tracking**: Local notifications and habit reminders to keep users on track.
*   **User Profile**: Comprehensive user data management and onboarding flow (`onboarding_glitch_intro`).

<a id="technology-stack"></a>

## 🛠️ Technology Stack

*   **Frontend Framework**: Flutter (Dart)
*   **State Management & Routing**: `provider`, `go_router`
*   **Local Database**: SQLite (`sqflite`) for on-device data storage.
*   **Backend & Cloud Services**: Firebase (Authentication, Cloud Functions).
*   **UI/UX**: Custom components, `flutter_animate`, `fl_chart` for data visualization, `lottie` for animations, and custom shaders.
*   **Native Integrations**: `pedometer`, `flutter_local_notifications`, `permission_handler`, `url_launcher`.
*   **Architecture**: Originates from/utilizes FlutterFlow patterns (as seen in `lib/flutter_flow/`).

<a id="project-structure"></a>

## 📂 Project Structure

```text
vytha_lab/
├── android/               # Android native project files
├── ios/                   # iOS native project files
├── web/                   # Web project files
├── functions/             # Firebase Cloud Functions (TypeScript)
├── lib/                   # Main Dart source code
│   ├── backend/           # Local SQLite database configurations
│   ├── components/        # Reusable UI widgets (cards, charts, buttons, etc.)
│   ├── flutter_flow/      # Base utilities and theme files from FlutterFlow
│   ├── models/            # Data models (e.g., biometrics_snapshot)
│   ├── pages/             # App screens (Dashboard, Meal Planner, Workout Tracker, etc.)
│   ├── services/          # Business logic and external service integrations
│   ├── app_state.dart     # Global application state
│   └── main.dart          # Application entry point
├── assets/                # Fonts, images, videos, audios, and JSON data
└── python_scripts         # Various utility scripts (e.g., fix_appbars.py, patch_onboarding.py) for codebase maintenance
```

<a id="getting-started"></a>

## 🏁 Getting Started

### Prerequisites

*   Install [Flutter SDK](https://flutter.dev/docs/get-started/install) (Ensure it meets the version requirement in `pubspec.yaml`: `>=3.0.0 <4.0.0`).
*   Install [Dart SDK](https://dart.dev/get-dart).
*   Set up an IDE (VS Code, Android Studio, or IntelliJ) with Flutter & Dart plugins.
*   *(Optional)* Install [Firebase CLI](https://firebase.google.com/docs/cli) if you need to deploy or test Cloud Functions.

### Installation

1.  **Clone the repository** (if you haven't already):
    ```bash
    git clone <repository-url>
    cd vytha_lab
    ```

2.  **Install Flutter dependencies**:
    ```bash
    flutter pub get
    ```

3.  **Install Firebase Cloud Functions dependencies** (if working on the backend):
    ```bash
    cd functions
    npm install
    cd ..
    ```

### Running the App

To run the app on an emulator, connected device, or web browser:

```bash
# Run on default device
flutter run

# Run on a specific device/platform
flutter run -d chrome
```

<a id="privacy-and-terms"></a>

## 🔒 Privacy & Terms

Vytha Lab handles personal wellness information, so privacy and responsible use should be treated as core product requirements. This section is a project-level notice and should be replaced with a reviewed Privacy Policy and Terms of Use before any public release.

<a id="privacy-policy-draft"></a>

### Privacy Policy Draft

This draft describes the intended privacy practices for Vytha Lab. It should be reviewed against the actual production build, connected services, app-store disclosures, and applicable laws before release. Public builds should provide an official privacy-policy URL, support contact, legal entity name, and in-app access to the final policy.

#### Scope

*   **Covered services**: This policy applies to the Vytha Lab Flutter app, local app storage, Firebase-backed features, Cloud Functions, AI-assisted nutrition features, notification features, pedometer integration, and related support workflows.
*   **Responsible party**: The final public policy should identify the developer, company, or legal entity responsible for user data.
*   **Health-data caution**: Vytha Lab handles wellness, fitness, nutrition, and biometric information. Do not describe the app as HIPAA-compliant, medically certified, or suitable for clinical use unless that status has been legally and technically validated.

#### Information Vytha Lab May Collect

*   **Account and profile data**: Name, email address, authentication identifiers, display preferences, onboarding responses, goals, biological or lifestyle attributes the user chooses to provide, and profile settings.
*   **Fitness and workout data**: Exercise history, workout sessions, custom routines, sets, reps, weights, duration, performance metrics, yoga sessions, recovery notes, and training preferences.
*   **Nutrition and AI inputs**: Meal-planning prompts, food preferences, allergies or restrictions entered by the user, macro targets, food logs, generated meal plans, and nutrition-analysis history.
*   **Biometric and progress data**: Body measurements, progress snapshots, evolution records, weight or composition entries, health-related notes, and progress photos if enabled by the app.
*   **Habit and reminder data**: Habit names, completion history, streaks, reminder schedules, local notification preferences, and wellness routines.
*   **Device and sensor data**: Step-count information from pedometer sensors, permission status, timezone data, device identifiers, platform details, and other data required for native integrations.
*   **Technical and diagnostic data**: App version, crash logs, performance diagnostics, Cloud Function logs, security events, and basic usage events if analytics or crash reporting are enabled.
*   **Support communications**: Messages, screenshots, bug reports, contact details, or other information users provide when requesting help.

#### How Data Is Collected

*   **Direct user input**: Data entered through onboarding, profile forms, trackers, planners, dashboards, and settings.
*   **Device permissions**: Data accessed through platform permissions such as sensors, notifications, or external-link handling. Users can manage permissions in their device settings.
*   **Generated data**: Calculations, summaries, charts, recommendations, and AI outputs created from user activity or user-provided inputs.
*   **Service integrations**: Data processed through Firebase, Cloud Functions, AI providers, analytics, crash reporting, or other configured third-party services.

#### How Data May Be Used

*   **Core app functionality**: Authenticate users, store preferences, track workouts, manage routines, display dashboards, calculate progress, and sync cloud-backed features.
*   **Personalization**: Adapt goals, nutrition suggestions, habit reminders, performance summaries, and UI content to user-provided preferences.
*   **AI-assisted features**: Generate meal plans, macro feedback, summaries, and wellness suggestions from the information users choose to submit.
*   **Notifications**: Schedule habit reminders, workout prompts, and local alerts selected by the user.
*   **Safety, debugging, and maintenance**: Diagnose issues, prevent abuse, protect accounts, maintain service reliability, and fix defects.
*   **Compliance**: Respond to lawful requests, enforce terms, and meet legal or regulatory obligations where applicable.
*   **Product improvement**: Analyze aggregated or de-identified information where possible to improve features, performance, and usability.

#### Sensitive Health Data Commitments

*   **Data minimization**: Collect only the wellness, fitness, biometric, nutrition, and sensor data needed for the features a user chooses to use.
*   **Consent before sensitive processing**: Obtain clear consent before collecting or sharing sensitive health data, especially when a feature uses device sensors, cloud processing, or third-party AI.
*   **No sale of health data**: Health, biometric, nutrition, and workout data should not be sold to data brokers or used for targeted advertising.
*   **No unexpected sharing**: Sensitive data should not be shared for marketing, advertising, model training, or unrelated product purposes unless the final policy clearly discloses it and the user gives explicit consent.
*   **Just-in-time notices**: Public builds should explain sensitive collection at the moment it occurs, not only inside this README or a long policy page.

#### AI and Cloud Processing

*   **AI data flow**: AI-powered meal planning and macro analysis may send user-provided goals, preferences, nutrition details, and related context to an AI service to generate results.
*   **Provider disclosure**: Public builds should identify each AI provider, what data is sent, whether the provider stores prompts or outputs, whether humans may review data, and whether data may be used for model training.
*   **Limited AI context**: AI requests should avoid unnecessary identifiers, account data, photos, or biometric details unless those inputs are required for the selected feature.
*   **User review**: AI output should be treated as a suggestion. Users remain responsible for checking nutrition, allergy, medical, and safety implications before acting on it.

#### Data Sharing

*   **Service providers**: Data may be processed by Firebase, hosting providers, authentication providers, Cloud Functions, AI vendors, analytics tools, crash reporting tools, or notification infrastructure used to operate the app.
*   **Legal and safety needs**: Data may be disclosed when required by law, to protect users, to investigate abuse, or to defend the rights and security of the app.
*   **Business changes**: If ownership of the app changes, user data may be transferred as part of that transaction, subject to notice and applicable law.
*   **No public posting by default**: Private health, nutrition, workout, and biometric records should not be made public unless the user intentionally chooses a sharing feature.
*   **Third-party terms**: Third-party services may process data under their own terms and privacy policies. Public builds should link to those providers where practical.

#### Storage, Retention, and Deletion

*   **Local storage**: Some records are stored on the user's device using SQLite or platform storage. Local data may remain on the device until the user deletes it, clears app data, or uninstalls the app.
*   **Cloud storage**: Firebase-backed features may store account, profile, function, or synced app data in cloud systems.
*   **Retention principle**: Data should be retained only for as long as needed to provide the app, comply with legal obligations, resolve disputes, maintain backups, or support security and debugging.
*   **Deletion requests**: Public builds should provide a clear way to request account deletion, cloud-data deletion, and correction of inaccurate personal data.
*   **Backup limits**: Deleted data may remain in encrypted backups or logs for a limited period before being purged according to the provider's retention process.

#### User Choices and Rights

*   **Access and correction**: Users should be able to view and update profile, goal, workout, nutrition, habit, and biometric information where the app supports it.
*   **Permission controls**: Users can revoke sensor, notification, and other platform permissions through device settings. Some features may stop working when permissions are disabled.
*   **AI controls**: Public builds should disclose whether AI features are optional and how users can avoid sending sensitive data to AI services.
*   **Analytics choices**: If non-essential analytics are enabled, public builds should explain opt-out controls where required.
*   **Legal rights**: Depending on location, users may have rights to access, delete, correct, export, restrict, or object to processing of personal information. The final policy should document how to exercise those rights.

#### Security

*   **Transport security**: Cloud traffic should use secure transport such as HTTPS/TLS.
*   **Access controls**: Cloud data should be protected with appropriate authentication, authorization rules, least-privilege service accounts, and secure secret management.
*   **Operational safeguards**: Production releases should include dependency review, logging hygiene, crash-report review, Firebase security-rule review, and incident-response procedures.
*   **No absolute guarantee**: No app can guarantee perfect security, so the final policy should explain security practices without overpromising.

#### Children and Minors

*   **Age limits**: Vytha Lab is not intended for children under 13, or under the minimum age required by local law, unless a parent or guardian provides any required consent.
*   **Minor data**: Public builds that knowingly support minors should include age-appropriate notices, parental consent flows, and child-data deletion procedures.
*   **Discovery of child data**: If the project owner learns that child data was collected without required consent, the data should be deleted or deactivated according to applicable law.

#### International Data Processing

*   **Cross-border processing**: Cloud providers, AI services, and support tools may process data in countries other than the user's country of residence.
*   **Safeguards**: Public builds should describe applicable transfer safeguards, regional hosting choices, and provider commitments where required by law.

#### Policy Changes

*   **Updates**: The privacy policy should be updated whenever the app's data collection, sharing, AI processing, analytics, permissions, or service providers change.
*   **Material changes**: If a change materially affects user privacy, users should receive clear notice and, where required, provide affirmative consent before the new use applies.
*   **Consistency**: The README, in-app policy, app-store privacy labels, Google Play Data Safety form, consent prompts, and actual app behavior should remain aligned.

#### Release Checklist

Before publishing Vytha Lab, add or verify:

*   Official legal entity name, contact email, and support/data-request process.
*   Final Privacy Policy URL available in the app and app-store listings.
*   Provider list for Firebase, AI services, analytics, crash reporting, and any SDKs.
*   Exact data-retention schedule for local data, cloud data, logs, and backups.
*   Account deletion and data deletion flow.
*   App Store privacy details and Google Play Data Safety disclosures matching the real build.
*   In-app consent prompts for health data, sensor access, AI processing, and optional analytics.

<a id="terms-of-use"></a>

### Terms of Use

These draft terms describe the expected rules for using Vytha Lab. They are intended for product documentation and should be reviewed before being presented to end users.

*   **Acceptance of terms**: By accessing or using Vytha Lab, users agree to use the app in accordance with these terms and any additional notices shown in the app.
*   **Wellness tool only**: Vytha Lab provides fitness, nutrition, habit, and wellness tracking support. It does not provide medical advice, diagnosis, treatment, emergency care, or a substitute for professional judgment.
*   **Professional guidance**: Users should consult qualified health professionals before making significant changes to exercise, diet, medication, treatment, or recovery plans, especially if they have existing health conditions.
*   **User responsibility**: Users are responsible for the information they enter, the goals they set, and how they apply workout, nutrition, habit, or AI-generated recommendations.
*   **AI-generated content**: Meal plans, macro analysis, coaching text, or other AI-assisted outputs may be incomplete, inaccurate, or unsuitable for a user's specific medical, dietary, cultural, or personal needs. Users should verify recommendations before relying on them.
*   **Account security**: Users are responsible for maintaining the confidentiality of their login credentials, device access, and any activity that occurs under their account.
*   **Permitted use**: Users may not misuse the app, attempt to disrupt its services, reverse engineer protected portions of the app, upload unlawful or harmful content, or use the app in a way that violates applicable laws or third-party rights.
*   **Health and sensor data**: Users authorize the app to process health, biometric, nutrition, workout, notification, and device-sensor data only for the features they choose to use, subject to the app's privacy notices and permission settings.
*   **Notifications**: Habit reminders, workout prompts, and other notifications are convenience features. Users remain responsible for managing their schedules, safety, and device settings.
*   **Third-party services**: Vytha Lab may rely on services such as Firebase, AI providers, analytics, crash reporting, device APIs, or external links. Those services may be governed by their own terms and privacy policies.
*   **Intellectual property**: The app, codebase, design assets, trademarks, content, and documentation belong to their respective owners. No rights are granted except as expressly allowed by the project owner or applicable licenses.
*   **Availability and changes**: Features may be changed, suspended, or removed during development. The app may contain bugs, incomplete features, or experimental behavior.
*   **No guarantee of results**: Fitness, nutrition, and wellness outcomes vary by individual, and the app does not guarantee specific results, performance improvements, health outcomes, or uninterrupted availability.
*   **Limitation of liability**: To the fullest extent permitted by law, the project owner and contributors are not responsible for indirect, incidental, consequential, or health-related damages arising from use of the app.
*   **Termination**: Access may be suspended or removed if a user violates these terms, creates security risk, misuses the service, or if the app is discontinued.
*   **Contact and legal review**: Public builds should include an official support contact, governing law, dispute-resolution process, and legally reviewed Privacy Policy and Terms of Use.
*   **Private package**: This repository is configured as a private package and is not currently licensed for public redistribution.

<a id="utility-scripts"></a>

## 📜 Utility Scripts

The project root contains several Python scripts (e.g., `fix_appbars.py`, `patch_onboarding.py`, `wrap_scaffold.py`). These are custom utility scripts likely used to perform bulk modifications, fix UI inconsistencies, or patch specific widget structures across the codebase. Run these with caution and ensure you review changes via Git.

<a id="license"></a>

## 📝 License

This project is configured as a private package (`publish_to: 'none'`).
