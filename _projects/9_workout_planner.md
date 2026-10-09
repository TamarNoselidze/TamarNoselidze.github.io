---
layout: page
title: "Workout Planner"
description: Multi-language console application implemented in both Java and C# to design, customise, and manage personalised workout routines and nutritional metrics with external API integration.
img: assets/img/gym.png
importance: 2
category: Personal Projects
related_publications: false
---

### Overview

The **Workout Planner** is a cross-platform console application designed to help users structure, customise, and maintain personalised fitness routines and nutritional profiles. Initially developed in **C#** and subsequently re-engineered in **Java**, the project demonstrates clean software architecture and data handling across both object-oriented ecosystems while maintaining identical functional capabilities and data schemas.

The application communicates with external REST APIs to source targeted workout movements and dietary targets, providing persistent local profiles for fitness tracking without requiring a complex database server.

- **Languages**: C# (.NET 6.0+), Java (JDK 16+)
- **Build & Dependency Management**: Visual Studio / .NET CLI, Apache Maven
- **Data Persistence**: JSON-based local state storage (`database.json`) via Newtonsoft.Json (C#) and Gson (Java)
- **External Services**: RapidAPI (ExerciseDB, WorkoutDB, Nutrition Calculator)

---

### Dual-Ecosystem Implementation

To explore architectural paradigms, dependency handling, and network requests across two mainstream enterprise platforms, the application was built with two standalone implementations:

- **C# Implementation**:
  - Developed against the **.NET 6.0+ SDK**.
  - Employs **Newtonsoft.Json** for serialization and deserialization of nested workout plans and user profiles.
  - Utilises asynchronous HTTP client patterns for reliable RESTful communication.
  - **Repository**: [TamarNoselidze/WorkoutPlanner](https://github.com/TamarNoselidze/WorkoutPlanner)

- **Java Implementation**:
  - Built with **Java 16+** and structured using **Apache Maven**.
  - Utilises Google's **Gson** library for mapping user records and API JSON responses into strongly typed domain model POJOs.
  - Packaged for execution via the Maven Exec Plugin (`mvn exec:java`).
  - **Repository**: [TamarNoselidze/Workout-Planner](https://github.com/TamarNoselidze/Workout-Planner)

---

### Key Capabilities

- **User Authentication & Session Management**: User registration and login flows enabling multiple distinct profiles to persist bespoke routines and biometric histories on a single system.
- **Exercise Directory & Custom Routines**: Searchable catalogue of exercises covering major muscle groups. Users can construct custom routines specifying targeted sets, repetitions, and rest intervals.
- **Goal-Oriented Suggestions**: Automated workout recommendations based on individual fitness objectives.
- **Biometric & Nutritional Profiling**: Computes body mass index (BMI), basal metabolic rate, and maintenance caloric expenditure according to height, weight, age, biological sex, and activity level.
- **Macronutrient & Micronutrient Guidance**: Breaks down recommended daily intakes into protein, carbohydrate, and fat targets, as well as essential vitamins and minerals.

---

### External API Integrations

The application integrates with three RESTful services hosted on RapidAPI:

1. **[ExerciseDB API](https://rapidapi.com/justin-WFnsXH_t6/api/exercisedb)**: Retrieves general exercises and instructions categorised by targeted muscle group.
2. **[WorkoutDB API](https://rapidapi.com/naeimsalib/api/work-out-api1)**: Queries tailored exercises according to specific muscle targets, available equipment, and intensity levels.
3. **[Nutrition Calculator API](https://rapidapi.com/sprestrelski/api/nutrition-calculator)**: Fetches detailed macronutrient and micronutrient profiles based on biometric inputs.

---

### Code & Repositories

- **C# Repository**: [TamarNoselidze/WorkoutPlanner](https://github.com/TamarNoselidze/WorkoutPlanner)
- **Java Repository**: [TamarNoselidze/Workout-Planner](https://github.com/TamarNoselidze/Workout-Planner)
