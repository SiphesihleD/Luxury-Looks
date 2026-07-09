# Luxury Looks — Multi-Tenant Beauty Salon Booking App

A native Android application that lets multiple independent beauty businesses (hairdressing, nail technicians, eyelash technicians) manage bookings, clients, and payments from a single shared platform — while keeping each business's data fully isolated.

Built as a final-year research project addressing a real problem: small beauty businesses relying on paper notebooks, calendars, and WhatsApp for scheduling, leading to no-shows, double bookings, and lost client history.

## Features

- **Multi-tenant architecture** — a single codebase serves multiple independent salons (e.g. Beauty Bliss, Glam Hub, Lash & Nails Co.) with isolated client and booking data
- **Real-time appointment booking** — clients browse services, pick a date/time, and book with live availability checks to prevent double-booking
- **Firebase Authentication** — secure login/registration for both clients and admins, with session persistence
- **Real-time sync with Firestore** — bookings, services, and client records update live across devices using snapshot listeners
- **Admin dashboard** — business owners manage their service catalogue, view/update bookings, and track basic analytics
- **Full CRUD** — services and appointments support create, read, update, and soft-delete operations
- **Automated reminders** — reduces no-shows by notifying clients ahead of their appointment

## Tech Stack

- **Language:** Java
- **Platform:** Android (Android Studio)
- **Backend:** Firebase Firestore (real-time database), Firebase Authentication
- **Architecture:** MVVM (Model-View-ViewModel) with a repository pattern
- **UI:** Android Navigation Component, Material Design components, ViewPager2 + BottomNavigationView

## Architecture

The app follows MVVM to keep UI, business logic, and data access cleanly separated:

- **`FirebaseRepository`** — single source of truth for all Firestore reads/writes (services, bookings)
- **ViewModels** (`AuthViewModel`, `BookingViewModel`, `ServiceManagementViewModel`, `AppointmentCRUDViewModel`) — expose `LiveData` to the UI and contain business logic, e.g. checking time-slot availability before confirming a booking
- **`SessionManager`** — handles local session persistence via `SharedPreferences`
- **`AppNavigation`** — centralises navigation logic using the Android Navigation Component, including auth-based routing (unauthenticated users are routed to login)

Multi-tenancy is enforced at the data layer, keeping each business's services, bookings, and client records logically separated within Firestore.

## Development Process

Built using an Agile incremental development methodology. Requirements were gathered through user research with 14 customers and 3 beauty professionals, and the app went through functional, usability, and edge-case testing (including offline booking, concurrent booking conflicts, and invalid input handling) before user acceptance testing.

## Setup

1. Clone the repo:
   ```bash
   git clone https://github.com/SiphesihleD/Luxury-Looks.git
   ```
2. Open the project in Android Studio.
3. Add your own `google-services.json` (from your Firebase project) into the `app/` directory.
4. Enable **Email/Password Authentication** and **Firestore** in your Firebase console.
5. Build and run on an emulator or physical device.

## Future Enhancements

- AI-driven booking behaviour prediction and analytics
- E-commerce integration for product sales
- Cross-platform expansion beyond Android
