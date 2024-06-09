# Android Project Technical Documentation

## Introduction

### Project Overview
This project is an Android application designed to [brief description of the project goals and features]. It leverages modern Android development practices to ensure a robust and scalable architecture.

## Tech Stack
- **Kotlin**: The primary programming language used.
- **Android SDK**: The software development kit used for building Android applications.
- **Other technologies/libraries**: Hilt, Ktor, and [other technologies].

## Architecture

### Clean Architecture
Our project follows the principles of Clean Architecture to promote separation of concerns and maintainability.

#### Overview
Clean Architecture divides the project into distinct layers:

## Layers

### 1. Entity
- **Model**: Defines the core business entities and their attributes.

### 2. Frameworks and Drivers
- **DI**: Manages dependency injection to provide necessary instances throughout the application.
- **Network**: Handles network operations, including API requests and responses.
  - **Model**: Defines data structures for network communication.
  - **Remote**: Implements remote data source interactions per usecase or feature.
- **UI**: Manages user interface components and interactions.
  - **Screen 1**: Displays a list of items.
  - **Screen 2**: Shows details of a selected item.

### 3. Interface Adapters
- **Gateway**: Acts as an intermediary between use cases and data sources.
- **Models**: Contains data transfer objects used for moving data between layers.
- **Paging**: Manages data pagination for efficiently loading large datasets.
- **Ports**: Defines interfaces for external systems and services.
- **ViewModel**: Prepares and manages data for presentation in the UI layer.

### 4. Usecase
- **Use Cases**: Encapsulates business logic and orchestrates the flow of data between entities and other layers.

### UI State Management
#### Overview
We use a combination of **MVI** (Model-View-Intent) and **MVVM** (Model-View-ViewModel) patterns for managing UI state. This helps in keeping the UI layer decoupled from the business logic.

#### Best Practices for UI State Management and Data Handling
In this section, we outline some best practices for managing UI state and handling data effectively.

1. **Avoid Nulls**: Prefer using optionals or CNs (Content and Non-Content) over nulls to represent the absence of a value in your application.

2. **Model Reception in UI State Holders**: UI state holders, such as fragments or activities, should focus on receiving their working models (UI state models) directly, while the ViewModel should handle any necessary mapping of data.

3. **Data Reaction in UI State Holders**: Avoid letting UI state holders make decisions on how to react to the data they receive. Instead, let the ViewModel handle such logic to keep the UI layer focused on presentation.

4. **Safe API Design for UI State Holders**: When designing APIs (interfaces) for UI state holders, ensure they are resilient to potential errors or bad decisions made by the ViewModel. Functions that may fail should return a result or another type of monad to handle such scenarios gracefully.

5. **Using `open val` in Sealed Classes**: In sealed classes, utilize `open val` instead of normal vals with private overriding properties. This practice ensures proper inheritance and extendability, especially when working with sealed class hierarchies.

### Package Structure
Packages are organized by features and layers to enhance modularity and ease of maintenance.


com.example.project
├── applevel
│   ├── data
│   ├── di
│   ├── domain
│   └── usecase
└── feature
    ├── entity
    │   └── model
    ├── frameworksanddrivers
    │   ├── di
    │   ├── network
    │   │   ├── model
    │   │   └── remote
    │   └── ui
    │   │   ├── screen 1 (ex: list)
    │   │   └── screen 2 (ex: details)
    ├── interfaceadapters
    │   ├── gateway
    │   ├── models
    │   ├── paging
    │   ├── ports
    │   └── viewmodel
    └── usecase
## Debugging
[Chucker](https://github.com/ChuckerTeam/chucker) will be used in debugging endpoints for staging and dev flavors

## Branch Naming
Branch name will be categorized by folder ex: feature, bugFix, enhancement and hotfix and followed by the branch name matching Jira's task

## Gradle

### Core libraries used
- globalstate:0.0.2
- helpers:0.0.1
- pagination:0.0.5
- datehandling:0.0.2
### kotlin DSL

### buildSrc

### Multi-module management
