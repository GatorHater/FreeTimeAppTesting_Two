# Vacation Planner App Development Workflow

This document outlines the development workflow for the Vacation Planner Android app, which helps users plan their trips by guiding them through a series of selections and storing their preferences.

## Project Setup

### Requirements
- Android Studio Meerkat (2024.3.2) or newer
- JDK 11
- Gradle 8.0+
- Google API credentials for Calendar integration

### Environment Setup
1. Clone the repository
2. Open the project in Android Studio
3. Sync Gradle files
4. Ensure you have Google API credentials in `src/main/assets/`

## Project Architecture

The app follows MVVM (Model-View-ViewModel) architecture with Jetpack Compose for UI:

- **UI Layer**: Compose screens and components
- **ViewModel Layer**: Manages UI state and business logic
- **Repository Layer**: Handles data operations
- **External Services**: Google Calendar, travel APIs

## Key Components

### SelectionViewModel

Central state holder for user selections throughout the app:

- Vacation type selections
- Date ranges
- Destination info
- Budget information
- Lodging preferences
- Transportation details

## Navigation

The app uses Compose Navigation to manage screen transitions following this flow:

> Login → Options → Free Time Selection → Date Range → Planner Type → Vacation Type →
> People Count → Destination → Budget → Lodging → Transportation → Vacation Summary →
> Plan Vacation (Activities, Lodging, Transportation)

## External Integrations

- Google Calendar API for scheduling
- Retrofit for API calls to travel services
- Potential integrations with Booking.com, Groupon, etc.

## Development Workflow

### 1. Adding a New Screen
- Create a new Composable function in a relevant package
- Add screen to navigation graph in MainActivity.kt:
  ```kotlin
  composable("new_screen_route") {
      NewScreen(navController, selectionViewModel)
  }
  ```
- Add navigation actions to/from the screen

### 2. Extending the ViewModel
- Add new state variables to SelectionViewModel:
  ```kotlin
  var newSelection by mutableStateOf("")
      private set

  fun updateNewSelection(selection: String) {
      newSelection = selection
  }
  ```

### 3. API Integration
- Create API interface using Retrofit:
  ```kotlin
  interface TravelService {
      @GET("endpoint")
      suspend fun getData(): Response<DataModel>
  }
  ```
- Create repository to handle API calls
- Connect repository to ViewModel

### 4. Google Calendar Integration
- Ensure Google API dependencies are correctly set up
- Use the Calendar API client to create/modify events
- Handle authentication and permissions

## Testing

- **Unit Tests**: Test ViewModels and repositories
  ```bash
  ./gradlew test
  ```
- **UI Tests**: Test Compose UI components
  ```bash
  ./gradlew connectedAndroidTest
  ```

## Build and Deploy

### Debug Build
```bash
./gradlew assembleDebug
```

### Release Build
1. Update version in build.gradle.kts
2. Generate signed APK/Bundle:
   ```bash
   ./gradlew bundleRelease
   ```
3. Test on release build
4. Deploy to Google Play

## Troubleshooting

### Common Issues
- Google API authentication problems: Verify credentials file
- Compose preview not working: Update to latest Compose tooling
- Navigation issues: Check for proper route naming and parameters

## Code Style Guidelines
- Follow Kotlin coding conventions
- Use Compose best practices
- Document public APIs
- Write tests for new features

## Resources
- [Jetpack Compose Documentation](https://developer.android.com/jetpack/compose)
- [Google Calendar API](https://developers.google.com/calendar)
- [Retrofit Documentation](https://square.github.io/retrofit/)
