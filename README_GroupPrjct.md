# DeadlineQ — Smart Deadline & Task Manager

> **INFO 4335 — Mobile Application Development | Final Group Project**
> Kulliyyah of Information and Communication Technology (KICT), IIUM
> Lecturer: Mohd Khairul Azmi Hassan

---

## Table of Contents

1. [Group Members](#1-group-members)
2. [Project Title](#2-project-title)
3. [Introduction](#3-introduction)
4. [Objectives](#4-objectives)
5. [Target Users](#5-target-users)
6. [Features & Functionalities](#6-features--functionalities)
7. [UI Mock-up](#7-ui-mock-up)
8. [Architecture / Technical Design](#8-architecture--technical-design)
9. [Data Model](#9-data-model)
10. [Flowchart / Sequence Diagram](#10-flowchart--sequence-diagram)
11. [References](#11-references)

---

## 1. Group Members

| # | Full Name | Matric Number | Assigned Role |
|---|-----------|---------------|---------------|
| 1 | Safi Abrar Ishaat | 2127075 | Project Lead & Firebase Integration (Auth + Firestore) |
| 2 | Muhammad Azamuddin bin Shahril | 2227153 | UI/UX Developer (Screens, Navigation & State Management) |
| 3 | Muhammad Ammar bin Mohamad Sukri | 2313279 | Feature Developer (Notifications, Categories & Recurring Deadlines) |

> **Task Division Summary**
>
> | Member | Responsibilities |
> |--------|-----------------|
> | Safi Abrar Ishaat | Firebase Auth (login/register), Firestore CRUD operations, app architecture, GitHub repository management, final report |
> | Muhammad Azamuddin bin Shahril | All UI screens (Home, Task Detail, Profile), routing with `go_router`, Provider state management, UI/UX design consistency |
> | Muhammad Ammar bin Mohamad Sukri | Push notification system (Firebase Cloud Messaging), category/tag system, recurring deadline logic, package integrations |

---

## 2. Project Title

**DeadlineQ — Smart Deadline & Task Manager**

---

## 3. Introduction

### Problem Statement

University students and working professionals frequently struggle to keep track of multiple concurrent deadlines across academic submissions, work tasks, and personal commitments. The consequence of missed deadlines ranges from academic penalties to professional setbacks. Existing general-purpose to-do apps are either too complex, too simplistic, or fail to provide timely, context-aware reminders.

### Motivation

There is a clear need for a focused, lightweight, and intuitive deadline management application that:

- Proactively notifies users of approaching deadlines rather than requiring them to manually check.
- Allows tasks to be meaningfully organised by category, priority, and recurrence.
- Is accessible on mobile — the device students and professionals carry at all times.

### Relevance

This application aligns with the Islamic value of *Amanah* (trustworthiness and responsibility) by helping users fulfil their obligations on time. It also adheres to the principle of *Itqan* (excellence in work), encouraging structured and disciplined time management. The app will be built as a Shariah-compliant productivity tool — free of inappropriate content, intrusive advertising, or unethical data practices.

---

## 4. Objectives

The application aims to accomplish the following specific and measurable objectives:

1. **O1** — Enable users to create, update, and delete deadline-based tasks with a title, description, due date/time, category, and priority level within the app.
2. **O2** — Deliver automated push notifications to users at configurable intervals (e.g., 1 day, 1 hour) before a deadline expires.
3. **O3** — Allow tasks to be organised under user-defined categories (e.g., Academic, Work, Personal) and tagged with a priority level (High, Medium, Low).
4. **O4** — Support recurring deadline configurations (daily, weekly, monthly) so that repeating obligations are automatically re-scheduled after completion.
5. **O5** — Persist all user data securely in Firebase Firestore with real-time synchronisation across sessions.
6. **O6** — Provide a clean dashboard that displays today's upcoming deadlines, overdue tasks, and completed tasks at a glance.

---

## 5. Target Users

### Primary Users

**University Students** — Particularly students managing multiple course assignments, project submissions, quizzes, and lab reports simultaneously. Students at IIUM and similar institutions deal with overlapping deadlines across multiple courses each semester.

### Secondary Users

**Working Professionals & Freelancers** — Individuals juggling project milestones, client deliverables, and internal reporting deadlines who need a mobile-first, distraction-free task tracker.

**General Public** — Any individual seeking a simple, reliable reminder system for personal appointments, bill payments, or recurring obligations.

---

## 6. Features & Functionalities

### 6.1 Core Modules

| Module | Description |
|--------|-------------|
| **Authentication** | Users register and log in using email and password via Firebase Authentication. Sessions are persisted across app launches. |
| **Dashboard / Home** | Displays a summary of today's deadlines, overdue tasks (highlighted in red), and upcoming tasks sorted by due date. |
| **Task Management** | Full CRUD (Create, Read, Update, Delete) for deadline tasks. Each task includes: title, description, due date & time, category, priority level, and recurrence setting. |
| **Category & Tagging** | Users can assign each task to a category (Academic, Work, Personal, or a custom label) and a priority level (High 🔴, Medium 🟡, Low 🟢). |
| **Recurring Deadlines** | Tasks can be set to recur on a daily, weekly, or monthly basis. Upon completion, the next occurrence is automatically generated. |
| **Push Notifications** | Firebase Cloud Messaging (FCM) triggers push notifications at user-defined intervals before a deadline (e.g., 24 hours and 1 hour prior). Notifications are delivered even when the app is closed. |
| **Task Detail View** | A dedicated screen for viewing and editing the full details of a single task, including its history of recurrences. |
| **Profile / Settings** | Users can update their display name, manage notification preferences, and log out. |

### 6.2 UI Components

- `BottomNavigationBar` — Primary navigation between Home, Tasks, and Profile screens.
- `FloatingActionButton` — Quick-access button for adding a new task from any screen.
- `ListView` with `Card` widgets — Used to display the task list with colour-coded priority indicators.
- `DatePicker` and `TimePicker` dialogs — For setting and editing task due dates.
- `DropdownButton` — For selecting category and recurrence type.
- `Switch` / `ToggleButton` — For toggling recurrence on/off and notification preferences.
- `SnackBar` / `AlertDialog` — For confirmation prompts (e.g., delete task) and feedback messages.

### 6.3 External Packages (from pub.dev)

| Package | Purpose |
|---------|---------|
| `flutter_local_notifications` | Scheduling and displaying local push notifications based on task due dates |
| `firebase_messaging` | Firebase Cloud Messaging for remote push notifications |
| `go_router` | Declarative named-route navigation across the app |
| `provider` | State management — managing task list state and user session state |
| `intl` | Date and time formatting (e.g., "Tuesday, 18 June 2026 — 11:59 PM") |
| `uuid` | Generating unique IDs for each task document in Firestore |

---

## 7. UI Mock-up

> 📌 **PLACEHOLDER — Screen 1: Splash / Login Screen**
> *Insert wireframe/mockup showing: app logo ("DeadlineQ"), email and password text fields, "Login" button, and "Register" link. Background should use the app's primary colour theme.*

---

> 📌 **PLACEHOLDER — Screen 2: Dashboard / Home Screen**
> *Insert wireframe/mockup showing: greeting header ("Assalamualaikum, [Name]"), a horizontal summary strip (Today: 3 tasks, Overdue: 1, Completed: 5), a vertically scrollable ListView of today's tasks displayed as Cards with colour-coded priority badges, due time, category label, and a BottomNavigationBar at the bottom.*

---

> 📌 **PLACEHOLDER — Screen 3: Add / Edit Task Screen**
> *Insert wireframe/mockup showing: a form with fields for Task Title (TextField), Description (multi-line TextField), Due Date (DatePicker), Due Time (TimePicker), Category (DropdownButton), Priority Level (DropdownButton: High / Medium / Low), Recurring Toggle (Switch) with frequency selector (DropdownButton: Daily / Weekly / Monthly), and a "Save Task" button.*

---

> 📌 **PLACEHOLDER — Screen 4: Task Detail Screen**
> *Insert wireframe/mockup showing: full task information displayed in a scrollable view — title, description, due date/time, category badge, priority indicator, recurrence status, and two action buttons: "Edit" and "Mark as Complete" / "Delete".*

---

> 📌 **PLACEHOLDER — Screen 5: All Tasks / Filter Screen**
> *Insert wireframe/mockup showing: a full task list with filter chips at the top (All / High / Medium / Low / Category filters), a search bar, and the sortable ListView of tasks. Each task card shows title, due date, priority colour, and category tag.*

---

> 📌 **PLACEHOLDER — Screen 6: Profile / Settings Screen**
> *Insert wireframe/mockup showing: user avatar placeholder, display name, email (read-only), notification preference toggles (e.g., "Notify 24 hours before", "Notify 1 hour before"), and a "Log Out" button.*

---

## 8. Architecture / Technical Design

### 8.1 Project Folder Structure

```
deadlineq/
├── lib/
│   ├── main.dart                  # App entry point, Firebase initialisation
│   ├── app.dart                   # MaterialApp, GoRouter configuration
│   ├── models/
│   │   ├── task_model.dart        # Task data class (title, dueDate, priority, etc.)
│   │   └── user_model.dart        # User data class
│   ├── providers/
│   │   ├── task_provider.dart     # Task state — list, CRUD, filtering
│   │   └── auth_provider.dart     # Auth state — login, logout, current user
│   ├── screens/
│   │   ├── splash_screen.dart
│   │   ├── login_screen.dart
│   │   ├── register_screen.dart
│   │   ├── home_screen.dart
│   │   ├── add_edit_task_screen.dart
│   │   ├── task_detail_screen.dart
│   │   ├── all_tasks_screen.dart
│   │   └── profile_screen.dart
│   ├── widgets/
│   │   ├── task_card.dart         # Reusable task list card widget
│   │   ├── priority_badge.dart    # Colour-coded priority indicator
│   │   ├── category_chip.dart     # Category label chip
│   │   └── deadline_summary.dart  # Dashboard summary strip
│   ├── services/
│   │   ├── firestore_service.dart # All Firestore CRUD operations
│   │   ├── auth_service.dart      # Firebase Auth methods
│   │   └── notification_service.dart # Local + FCM notification scheduling
│   └── utils/
│       ├── constants.dart         # App-wide constants (colours, strings)
│       ├── date_helper.dart       # Date formatting and comparison utilities
│       └── validators.dart        # Form validation functions
├── android/
├── ios/
├── pubspec.yaml
└── README.md
```

### 8.2 State Management — Provider

The application uses the **Provider** package for state management. This approach was selected for its simplicity, testability, and suitability for a project of this scale.

```
Widget Tree
│
├── MultiProvider (root)
│   ├── ChangeNotifierProvider<AuthProvider>
│   │   └── Manages: login state, current user, logout
│   └── ChangeNotifierProvider<TaskProvider>
│       └── Manages: task list, CRUD operations, filter/sort state
│
└── Screens consume state via:
    └── context.watch<TaskProvider>()   — rebuilds on change
    └── context.read<TaskProvider>()    — triggers actions (no rebuild)
```

### 8.3 Navigation — go_router

Named routes are defined centrally in `app.dart`:

| Route Name | Path | Screen |
|------------|------|--------|
| `/` | `/` | `SplashScreen` |
| `login` | `/login` | `LoginScreen` |
| `register` | `/register` | `RegisterScreen` |
| `home` | `/home` | `HomeScreen` |
| `add-task` | `/tasks/add` | `AddEditTaskScreen` |
| `edit-task` | `/tasks/edit/:id` | `AddEditTaskScreen` |
| `task-detail` | `/tasks/:id` | `TaskDetailScreen` |
| `all-tasks` | `/tasks` | `AllTasksScreen` |
| `profile` | `/profile` | `ProfileScreen` |

### 8.4 Firebase Services Used

| Firebase Service | Usage in DeadlineQ |
|------------------|--------------------|
| **Firebase Authentication** | Email/password registration and login; session persistence |
| **Cloud Firestore** | Storing and querying all task documents per user in real-time |
| **Firebase Cloud Messaging (FCM)** | Sending push notifications for approaching deadlines |

---

## 9. Data Model

### 9.1 Firestore Collection Structure

```
Firestore Root
│
└── users/                         (Collection)
    └── {userId}/                  (Document — one per authenticated user)
        ├── displayName: String
        ├── email: String
        ├── notifyBefore24h: Boolean
        ├── notifyBefore1h: Boolean
        │
        └── tasks/                 (Sub-collection)
            └── {taskId}/          (Document — one per task)
                ├── taskId: String        (UUID)
                ├── title: String
                ├── description: String
                ├── dueDate: Timestamp
                ├── category: String      ("Academic" | "Work" | "Personal" | custom)
                ├── priority: String      ("High" | "Medium" | "Low")
                ├── isRecurring: Boolean
                ├── recurrenceType: String ("daily" | "weekly" | "monthly" | null)
                ├── isCompleted: Boolean
                ├── createdAt: Timestamp
                └── updatedAt: Timestamp
```

### 9.2 Entity Relationship Diagram (ERD)

> 📌 **PLACEHOLDER — ERD Diagram**
> *Insert ERD diagram showing two entities:*
> - ***User** (userId PK, displayName, email, notifyBefore24h, notifyBefore1h)*
> - ***Task** (taskId PK, userId FK, title, description, dueDate, category, priority, isRecurring, recurrenceType, isCompleted, createdAt, updatedAt)*
> - *Relationship: One User has many Tasks (1 to N). Draw using standard ERD notation (crow's foot or Chen notation).*

---

## 10. Flowchart / Sequence Diagram

### 10.1 User Authentication Flow

> 📌 **PLACEHOLDER — Flowchart: Authentication Flow**
> *Insert flowchart showing:*
> *START → App Launches → Check Auth State → [If Authenticated] → Home Screen → END*
> *→ [If Not Authenticated] → Login Screen → [User submits credentials] → Firebase Auth validates → [Success] → Home Screen → END*
> *→ [Failure] → Show error SnackBar → Return to Login Screen*

---

### 10.2 Task Creation & Notification Scheduling Flow

> 📌 **PLACEHOLDER — Flowchart: Add Task & Notification Flow**
> *Insert flowchart showing:*
> *User taps FAB → Add Task Screen → User fills form → Validates inputs → [Invalid] → Show field errors → [Valid] → Save to Firestore → Check isRecurring → [Yes] → Store recurrence config → Schedule Local Notifications (flutter_local_notifications) for due time → FCM token registered → END*
> *→ [No] → Schedule notification only → END*

---

### 10.3 App Navigation Sequence Diagram

> 📌 **PLACEHOLDER — Sequence Diagram: Full Navigation Flow**
> *Insert sequence diagram with actors: User, App (Flutter), Firebase Auth, Firestore, Notification Service.*
> *Show the sequence: User opens app → App checks Auth → Firebase returns auth state → If logged in: App fetches tasks from Firestore → Tasks rendered on HomeScreen → User adds task → App writes to Firestore → App schedules notification → Notification Service confirms → App shows success message.*

---

### 10.4 Recurring Deadline Logic Flow

> 📌 **PLACEHOLDER — Flowchart: Recurring Task Completion Flow**
> *Insert flowchart showing:*
> *User marks task as complete → App checks isRecurring → [No] → isCompleted = true → Firestore updated → END*
> *→ [Yes] → Calculate next due date based on recurrenceType (daily +1 day / weekly +7 days / monthly +1 month) → Create new task document in Firestore with new dueDate → Schedule new notification → Mark original as completed → END*

---

## 11. References

1. Flutter Team. (2024). *Flutter Documentation*. Google LLC. https://docs.flutter.dev
2. Firebase Team. (2024). *Firebase Documentation — Cloud Firestore*. Google LLC. https://firebase.google.com/docs/firestore
3. Firebase Team. (2024). *Firebase Authentication Documentation*. Google LLC. https://firebase.google.com/docs/auth
4. Firebase Team. (2024). *Firebase Cloud Messaging (FCM) Documentation*. Google LLC. https://firebase.google.com/docs/cloud-messaging
5. pub.dev. (2024). *flutter_local_notifications package*. https://pub.dev/packages/flutter_local_notifications
6. pub.dev. (2024). *go_router package*. https://pub.dev/packages/go_router
7. pub.dev. (2024). *provider package*. https://pub.dev/packages/provider
8. pub.dev. (2024). *firebase_messaging package*. https://pub.dev/packages/firebase_messaging
9. pub.dev. (2024). *intl package*. https://pub.dev/packages/intl
10. pub.dev. (2024). *uuid package*. https://pub.dev/packages/uuid
11. Google LLC. (2024). *Material Design 3 Guidelines*. https://m3.material.io
12. GitHub Docs. (2024). *Basic writing and formatting syntax (Markdown Guide)*. https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
13. Flutter Team. (2024). *State Management Options — Flutter Docs*. https://docs.flutter.dev/data-and-backend/state-mgmt/options

---

> *Prepared by Group [Your Group Number] | INFO 4335 — Mobile Application Development | KICT, IIUM | June 2026*
