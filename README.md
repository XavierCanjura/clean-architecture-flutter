# structure_base

This project is an example how to order the project folders using Clean Architecture

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

## Structure Folder - Clean Architecture

```bash
📁lib/
├── 📁core/ 
|   ├── 📁helper/
|   ├── 📁network/
|   ├── 📁router/
|   ├── 📁theme/
|   ├── 📁translations/
|   ├── 📁services/
|   └── 📁utils/
|       ├── 📁constant/
|       ├── 📁validators/
|       └── injections.dart
├── 📁features/
|   ├── 📁auth/
|   |   ├── 📁data/ or infrastructure/
|   |   |   ├── 📁datasources/
|   |   |   ├── 📁graphql/
|   |   |   ├── 📁mappers/
|   |   |   ├── 📁models/
|   |   |   └── 📁repositories/
|   |   ├── 📁domain/
|   |   |   ├── 📁datasources/
|   |   |   ├── 📁entities/ or models/
|   |   |   ├── 📁usecases/
|   |   |   └── 📁repositories/
|   |   ├── 📁presentation/
|   |   |   ├── 📁pages/
|   |   |   ├── 📁providers/ or bloc/
|   |   |   └── 📁widgets/
|   |   └── auth_injections.dart
|   └── 📁.../
├── 📁shared/
|   ├── 📁data/
|   ├── 📁domain/
|   ├── 📁presentation/
|   └── app_injections.dart
└── main.dart
```

## Core
The `core` folder is a fundamental module housing key components like utils, routes, network, services, validators, and theme, and others. Its content can be tailored by developers to improve code cleanliness and adapt to evolving project needs, ensuring simplicity, modularity, and ease of maintenance.

`injection` file containe all injection methods feature, and it is called from the main.dart


## Features

`features` folder will contian all app features such as auth, profile, product..., and each feature of the application is built on the basis layers (Presentation, Domain, Data).

### 1. Presentacion Layer
---

### Responsibility
The presentation Layer is the outermost layer, responsible for presenting information to the user and capturing user interactions. It includes all the components related to the user interface (UI), such as widgets, screens, and presenters/controllers (State Management).

### Components
- **Pages**: Represent the feature screens.
- **Widgets**: Represent the visual elements of the aplication like buttons, fields, alerts, and others.
- **Manager/Controller**: Contain the presentation logic that interacts with the UI components. they receive user input, communicate with the Use Cases in the Doamin Layer, and update the UI accordingly.

  *The Manager/Controller layer can incorparate any state management solution, such as BloC, Riverpod, Provider, and others.* 

### 2. Domain Layer 
---
### Responsibility
the Domain Layer, also known as the business Logic or Use Case Layer, contains the core business rules and logic of the application, It represents the heart of the software system, encapsulating the essential functionality that is independent of any particular framework.

### Components

- **Entities**: Represent the fundamental business objects or concepts.
- **Use Cases**: Contian application-specific business rules and orchestrate the flow of data between entities. They are responsible for executing specific actions or operations.
- **Repositories**: Abstract interfaces that define how data is accessed and stored.
-- **Data Sources**: Define all the methods responsible for fetching data from the API or local database

### 3. Data Layer
---
### Responsibility
The Data layer is responsible for interacting with external data sources, such as databases, network services, or repositories. It handles the storage and retrieval of data

### Components
- **Business rules and Logic (Repository)**: Core functionality that is crucial to the application's domain
- **Data Models**: Represent the strucuture of the data as it stored in the external data sources
- **Data Sources**: Implementations of repositories that interact with databases, APIs, or other external services.

## Shared
Finally, the `shared` folder, it is like features folder but for common feature in our application, like payment feature, shared pages, shared widgets, abd othders."