# Pak Livestock Care (موبائل لائیو سٹاک پورٹل)

Pak Livestock Care is an AI-powered pastoral mobile resource portal designed for farmers, livestock administrators, and veterinarians in Pakistan. The application coordinates local meteorological metrics with Jetpack Room storage persistence, customized Google Sign-In authentication, and Gemini AI's powerful analytical capabilities to provide real-time herd health monitoring, medical diagnostic scanning, weather-correlated fodder crop feeds, and regional clinic registries.

With its **Pastoral Fields** (light mode) and **Cosmic Fields** (dark mode) Material Design 3 styling, the app delivers a highly tactile, responsive, and bilingual (English and Urdu) registry system.

---

## 📱 App Experience & Screenshots
The interface utilizes an ergonomic **Single-Screen Adaptive Container** featuring top high-contrast indicators, Material 3 bottom navigation, dynamic alert state layouts, and context-aware action triggers.

*   **Header Bar**: Prominent district indicator, real-time localized weather stats, and user account credentials with custom secure logouts.
*   **Google Sign-In Console**: Secure authentication via standard Google Services with a fast Web Login alternate fallback.
*   **Bilingual Console**: Urdu and English instruction models across medical scanners, alerts, and help centers.

---

## 🛠️ Core Capabilities

### 1. Secure Google Authentication
*   **Single Sign-on Integration**: Fully coupled with `play-services-auth` APIs to securely log users into their profile registry.
*   **Web Fallback Account Selector**: A dynamic Web Login popup interface allowing manual credentials setup which lets users sign in safely on devices missing Google Play Services.
*   **Localized Context Tracking**: Pre-selects and links the farm's active geographic district during login to customize weather and fodder feeds immediately.

### 2. Live Weather Warning & Heat Stress (THI) Index
*   **THI Calculator**: Implements the standardized **Temperature Humidity Index (THI)** calculation using real-time temperature and relative humidity.
*   **Dynamic Alerting Levels**:
    *   **Normal / Comfortable**: Healthy parameters for grazing.
    *   **Alert / Mild Stress**: Guidance on shadowing and fresh water access.
    *   **Danger / Extreme Stress**: Immediate alert protocols to mitigate dry-matter intake declines and milk yield loss.
*   **Local Outbreak Risk Card**: Tracks local parameters for vector-borne diseases such as **Bluetongue Virus**, **Foot and Mouth Disease (FMD)**, or **Rinderpest** tailored to the active district.

### 3. AI physical Health Scanning (Gemini API)
*   **Multi-Species Diagnostics**: Supports visual health reviews for cows, bulls, buffaloes, sheep, goats, and fat-tailed dumba (*Dumba*).
*   **Diagnosis Engine**: Allows uploading local media files or selecting active symptom-based image presets (e.g., active foot rot, mouth sores, dermal rashes, bloating).
*   **Gemini Diagnostics output**: Analyzes severity levels, suggests immediate isolation procedures, lists quarantine parameters, and recommends specific local vets.

### 4. Interactive Livestock Database (Room Storage)
*   **Local Caching Schema**: Implements structured tables using Jetpack Room (`AnimalEntity` and `VaccineRecordEntity`) for offline-friendly registers.
*   **Herd Registry**: Direct enrollment workflows including detailed fields for:
    *   Animal tag names (e.g., *Sahiwal Gold*)
    *   Animal Type (Cow, Buffalo, etc.)
    *   Specific Breed (Sahiwal Cow, Cholistani, Nili Ravi Buffalo, Beetal, etc.)
    *   Age in months & precise geographic farmed district.
*   **Surgical Vaccine Ledger**: Tracks immunization history (vaccine name, execution date, administrating doctor/department) linked directly to the animal database.

### 5. Weather-Correlated Fodder Guides & Vet Clinic Registry
*   **Nutritional Planner**: Generates recommendations for crop selection (Berseem Clover, Alfalfa, Sorghum, Maize) optimized dynamically based on temperature and moisture levels.
*   **District Clinics Index**: Connects users to veterinary clinics, emergency government helplines, and municipal departments matching their localized district.

### 6. Interactive Bilingual AI Support Chat (English & Urdu)
*   **Gemini Chat Console**: Ask custom herd queries, health advice, or general management tips.
*   **Context-Aware Chat**: Feeds the active animal roster totals and localized weather stats into the Gemini window, allowing the AI to answer specific questions about *your* herd.
*   **Markdown Support**: Uses a customized Compose markdown renderer to output clean, structured titles, bullet points, and highlight warnings on small screens.

---

## 🏛️ Project Architecture

The codebase strictly adheres to Android **MVVM (Model-View-ViewModel)** guidelines and modern Kotlin structuring:

```
app/src/main/java/com/example/
├── MainActivity.kt                # Primary Entry Point and Compose views layout
├── data/
│   ├── api/
│   │   └── GeminiClient.kt        # Multi-modal REST wrapper for Gemini models
│   ├── local/
│   │   ├── AnimalEntity.kt        # Room Database Schema Definitions
│   │   ├── LivestockDao.kt       # Persistent Database Queries Contract
│   │   ├── LivestockDatabase.kt  # Local SQLite Database Builder Configuration
│   │   └── LivestockRepository.kt# Single Source of Truth for Data Streams
│   └── weather/
│       ├── WeatherService.kt      # District-wise Meteorology REST Client
│       └── WeatherRiskManager.kt  # Core business logic for THI & Regional Clinics
└── ui/
    ├── LivestockViewModel.kt      # Single reactive UI State holder model
    └── theme/
        ├── Color.kt               # Pastoral & Cosmic dynamic color mappings
        ├── Theme.kt               # Dynamic Material 3 System Configuration
        └── Type.kt                # Display typography mappings
```

---

## 🚀 Tech Stack & Library Dependencies

*   **Jetpack Compose**: 100% declarative UI components layout.
*   **Material Design 3**: Modern color styling with light theme (**Pastoral Fields**) representing lush grazing lands and dark theme (**Cosmic Fields**) for nighttime low-contrast environments.
*   **Android Room Database**: Multi-table local persistent storage structured with foreign key relationships for vaccine management.
*   **Kotlin Coroutines & Flow**: High-performance, non-blocking asynchronous operation streaming.
*   **Gemini LLM (Flash 1.5/2.0)**: Used for responsive bilingual chatting and intelligent multi-modal physical scans.
*   **Google Play Services Auth**: Cryptographically signs users in using certified Android Account Managers.
*   **Retrofit & OkHttp**: Networking library for loading live regional parameters.

---

## ⚙️ Configuration & Installation Setup

### Prerequisite Environment Properties
Sensitive credentials are authenticated of secure environmental properties (BuildConfig). Ensure your variables are specified correctly in your system parameters or Secrets panel:

1.  **API Key Configuration**: Ensure your `GEMINI_API_KEY` is registered in your developer secrets to unlock conversational and diagnostic diagnostics components.
2.  **Google Services Plugin**: The project is integrated with `google-services` build plugins. The app directory contains a base `google-services.json` designed for compilation. Update this JSON file to point to your live Google Firebase project.

### Step-by-Step Local Compilation
To compile the application locally:
```bash
# 1. Clone the project repository
git clone <repository-url>

# 2. Build of Gradle Wrapper or standard gradle task configs
gradle assembleDebug

# 3. Trigger tests to verify functional code paths
gradle :app:testDebugUnitTest
```

---

## ♿ Accessibility & Design Precision
*   **Touch Target Minimums**: All clickable elements, text input dropdowns, and button boxes are padded to exceed the **48dp x 48dp** Material Standard.
*   **Input Usability**: Customized disabled text fields styled with high-contrast Material colors enable easy dropdown activation without activating native keypads.
*   **Readable Typography**: Consistent baseline spacing grid paired with high-quality icons makes visual scanning comfortable for rural operators.
