# FitBuddy

A modern Android fitness tracking application built with Jetpack Compose, Firebase, and Kotlin.

## Overview

FitBuddy is a feature-rich fitness companion app that helps users track their workouts, view their exercise history, and get motivated with inspirational quotes. The app leverages modern Android development practices and technologies for a seamless user experience.

## Features

- **Workout Logging**: Easily log your workouts with exercise name, reps, and duration
- **Workout History**: View all your logged workouts in a historical timeline
- **Motivational Quotes**: Get inspired with random motivational quotes fetched from an API
- **Bluetooth Connectivity**: Built-in support for Bluetooth wearables integration
- **Firebase Integration**: Cloud storage for user workouts using Firebase Firestore
- **User Authentication**: Secure authentication powered by Firebase Auth
- **Modern UI**: Beautiful and intuitive interface built with Jetpack Compose Material3

## Tech Stack

### Core Technologies
- **Language**: Kotlin
- **UI Framework**: Jetpack Compose with Material 3
- **Minimum API Level**: 24 (Android 7.0)
- **Target API Level**: 34 (Android 14)
- **JVM Target**: Java 17

### Libraries & Frameworks

#### Architecture & Dependency Injection
- **Hilt**: Dependency injection framework for Android
- **Android ViewModel**: Lifecycle-aware viewmodel architecture

#### Navigation
- **Jetpack Navigation Compose**: Type-safe navigation for Compose apps
- **Hilt Navigation Compose**: Hilt integration with Compose navigation

#### Database & Backend
- **Firebase Firestore**: NoSQL cloud database for storing workout data
- **Firebase Authentication**: User authentication and management
- **Firebase Cloud Messaging**: Push notification support (via Firebase BOM)

#### Networking
- **Retrofit**: REST API client library
- **Gson Converter**: JSON serialization/deserialization for Retrofit

#### UI Components
- **Jetpack Compose**: Modern declarative UI framework
- **Material 3**: Latest Material Design system
- **Android Material**: Legacy Material Design components

#### Utilities
- **JavaPoet**: Code generation library (v1.13.0)
- **Core KTX**: Kotlin extensions for Android Core
- **Lifecycle Runtime KTX**: Kotlin extensions for lifecycle components

#### Testing
- **JUnit**: Unit testing framework
- **Espresso**: UI testing framework
- **Compose UI Testing**: Testing utilities for Compose

## Project Structure

```
FitBuddy/
├── app/
│   ├── build.gradle.kts              # App module build configuration
│   ├── google-services.json           # Firebase configuration
│   ├── proguard-rules.pro            # ProGuard obfuscation rules
│   └── src/
│       ├── main/
│       │   ├── AndroidManifest.xml   # App manifest
│       │   ├── java/com/example/fitbuddy/
│       │   │   ├── FitBuddyApp.kt           # Hilt application entry point
│       │   │   ├── MainActivity.kt           # Main activity with navigation
│       │   │   ├── data/
│       │   │   │   ├── model/
│       │   │   │   │   └── Workout.kt       # Data class for workout model
│       │   │   │   └── remote/
│       │   │   │       ├── Quote.kt         # Quote data model
│       │   │   │       ├── QuoteApiService.kt  # Retrofit API service
│       │   │   │       └── RetrofitClient.kt   # Retrofit client setup
│       │   │   ├── ui/
│       │   │   │   └── theme/
│       │   │   │       ├── Color.kt         # App color definitions
│       │   │   │       ├── Theme.kt         # Compose theme configuration
│       │   │   │       ├── Type.kt          # Typography definitions
│       │   │   │       └── screens/
│       │   │   │           ├── HomeScreen.kt        # Home screen
│       │   │   │           ├── LogWorkoutScreen.kt  # Workout input screen
│       │   │   │           ├── HistoryScreen.kt     # Workout history display
│       │   │   │           └── QuoteScreen.kt       # Quote display screen
│       │   │   └── viewmodel/
│       │   │       └── WorkoutViewModel.kt  # ViewModel for workout management
│       │   └── res/
│       │       ├── drawable/          # Vector drawables
│       │       ├── mipmap-*/          # App icons (various densities)
│       │       ├── values/
│       │       │   ├── colors.xml     # Color resources
│       │       │   ├── strings.xml    # String resources
│       │       │   └── themes.xml     # Theme definitions
│       │       └── xml/
│       │           ├── backup_rules.xml      # Backup configuration
│       │           └── data_extraction_rules.xml  # Data extraction rules
│       ├── test/                      # Unit tests
│       └── androidTest/               # Instrumented tests
├── gradle/                            # Gradle wrapper configuration
├── build.gradle.kts                   # Root build configuration
├── settings.gradle.kts                # Project settings
└── gradle.properties                  # Gradle properties
```

## Key Components

### FitBuddyApp
The application entry point annotated with `@HiltAndroidApp` for Hilt dependency injection setup.

### MainActivity
Hosts the main Compose UI with:
- Navigation controller for screen navigation
- Drawer state management
- App scaffold with navigation structure

### WorkoutViewModel
Manages workout data and business logic:
- Loads and stores workouts from Firebase Firestore
- Manages loading and error states
- Exposes data through Kotlin Flows for reactive UI updates

### Screens
- **HomeScreen**: Main landing page with navigation options
- **LogWorkoutScreen**: Form to input new workout data
- **HistoryScreen**: Displays all logged workouts
- **QuoteScreen**: Fetches and displays motivational quotes from API

### Data Models
- **Workout**: Represents a single workout entry with name, reps, and duration
- **Quote**: Represents a motivational quote from the API

## Permissions

The app requires the following permissions:

- **INTERNET**: For REST API calls and Firebase connectivity
- **BLUETOOTH**: For Bluetooth wearable device connectivity
- **BLUETOOTH_ADMIN**: For administrative Bluetooth operations
- **BLUETOOTH_SCAN**: For scanning Bluetooth devices (never for location)
- **BLUETOOTH_CONNECT**: For Bluetooth device connection

## Getting Started

### Prerequisites
- Android Studio (latest)
- JDK 17 or higher
- Android SDK with API level 34

### Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd FitBuddy
   ```

2. **Configure Firebase**
   - Download your `google-services.json` from Firebase Console
   - Place it in `app/` directory

3. **Build and Run**
   ```bash
   ./gradlew build
   ./gradlew installDebug
   ```

   Or simply use Android Studio:
   - Open the project in Android Studio
   - Click "Run" or press `Shift + F10`

## Architecture

The app follows the Model-View-ViewModel (MVVM) architecture pattern:

- **Model**: Data classes (`Workout`, `Quote`) and Firestore operations
- **View**: Composable UI functions organized by screen
- **ViewModel**: `WorkoutViewModel` handling state and business logic

### Dependency Injection

Hilt is used throughout the app for:
- ViewModel injection
- Firebase service injection
- Retrofit API service injection

## Firebase Setup

1. Create a Firebase project at [Firebase Console](https://console.firebase.google.com)
2. Enable:
   - Authentication (Email/Password or your preferred methods)
   - Firestore Database (with appropriate security rules)
3. Download and add `google-services.json` to the app module

## Building & Testing

### Build
```bash
./gradlew build
```

### Run Tests
```bash
./gradlew test                  # Unit tests
./gradlew connectedAndroidTest  # Instrumented tests
```

### Build Release APK
```bash
./gradlew assembleRelease
```

## Code Style & Best Practices

- **Kotlin**: Modern Kotlin syntax with coroutines
- **Compose**: Declarative UI composition with state management
- **Type Safety**: Leveraging Kotlin's type system
- **Coroutines**: Async operations with Flow for reactive programming
- **Resource Management**: Proper Lifecycle handling with ViewModels

## Future Enhancements

- [ ] User profile and authentication UI
- [ ] Workout statistics and analytics
- [ ] Goal setting and tracking
- [ ] Social features (share workouts)
- [ ] Wearable integration (step tracking, heart rate)
- [ ] Workout plans and recommendations
- [ ] Offline support with local database
- [ ] Dark mode support

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is provided as-is for educational and personal use.

## Support

For issues, questions, or suggestions, please create an issue in the repository.

---

**Happy Training! 💪**
