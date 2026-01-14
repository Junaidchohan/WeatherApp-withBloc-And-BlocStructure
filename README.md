🌦 Weather App using Flutter BLoC Architecture

A Flutter weather application built with BLoC state management and clean architecture principles.
The main goal of this project is to demonstrate scalable state management, proper separation of concerns, and production ready BLoC pattern usage.

## 📸 App Screenshot

![Weather App UI](assets\screenshots\weather_app_ui.png)


```
🚀 Key Objectives of This Project
Implement BLoC pattern for predictable and testable state management
Apply clean architecture with clear separation of UI, business logic, and data layers
Handle asynchronous API calls using BLoC events and states
Build a maintainable and scalable Flutter application structure

🧠 Architecture Overview
This project follows a layered architecture combined with BLoC pattern:

lib/
│
├── bloc/
│   ├── weather_bloc.dart
│   ├── weather_event.dart
│   └── weather_state.dart
│
├── data/
│   └── data_provider/
│       └── weather_data_provider.dart
│
├── repository/
│   └── weather_repository.dart
│
├── models/
│   └── weather_model.dart
│
├── presentation/
│   ├── screens/
│   │   └── weather_screen.dart
│   └── widgets/
│       ├── additional_info_item.dart
│       └── hourly_forecast_item.dart
│
└── main.dart

🔁 BLoC Pattern Explanation
Event Layer
Defines what happens in the app.

sealed class WeatherEvent {}
final class WeatherFetched extends WeatherEvent {}

WeatherFetched is triggered when the app starts or when the user refreshes data.
State Layer
Defines how the UI should react.
sealed class WeatherState {}

class WeatherInitial extends WeatherState {}
class WeatherLoading extends WeatherState {}
class WeatherSuccess extends WeatherState {}
class WeatherFailure extends WeatherState {}


State responsibilities:
WeatherInitial → Initial state
WeatherLoading → API request in progress
WeatherSuccess → Weather data loaded successfully
WeatherFailure → Error occurred
BLoC Layer
Handles business logic and state transitions.
class WeatherBloc extends Bloc<WeatherEvent, WeatherState>


Responsibilities:
Listens for WeatherFetched event
Calls repository for data
Emits loading, success, or failure states
Keeps UI completely free from business logic

📦 Repository Pattern

The repository acts as a single source of truth for data.

class WeatherRepository {
  Future<WeatherModel> getCurrentWeather()
}


Why this matters:
UI does not depend on API implementation
Easy to swap API or add caching later
Improves testability

🌐 Data Provider Layer

Handles external API communication only.

class WeatherDataProvider {
  Future<String> getCurrentWeather(String cityName)
}


Responsibilities:
Makes HTTP request
Returns raw API response
No business logic

🧩 Model Layer
WeatherModel converts raw JSON into a strongly typed Dart object.

Benefits:
Type safety
Clean data handling
Easy debugging and maintenance

🎨 Presentation Layer
Uses BlocBuilder to react to state changes.
BlocBuilder<WeatherBloc, WeatherState>


UI behavior:
Shows loader during WeatherLoading
Displays weather data on WeatherSuccess
Shows error message on WeatherFailure
The UI never calls APIs directly.
It only reacts to state changes. This is proper BLoC usage.

🛠 Dependency Injection

Handled using RepositoryProvider and BlocProvider.

RepositoryProvider(
  create: (_) => WeatherRepository(WeatherDataProvider()),
)


This ensures:
Loose coupling
Clean dependency flow
Easy scalability

✅ Why This Project Matters
This project demonstrates:
Real world BLoC architecture
Clean separation of concerns
Production ready Flutter structure
Proper async state handling
Scalable and maintainable codebase
This is not a beginner level counter app.
This is the foundation used in professional Flutter applications.

📌 Next Improvements
Add unit tests for BLoC
Make city name dynamic
Add caching with local storage
Improve error handling
Implement pagination for hourly forecast

👤 Author
Muhammad Junaid
Flutter Developer | BLoC State Management
Think beyond boundaries 🚀
