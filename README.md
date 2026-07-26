# Portfolio App

This project is a simple Flutter portfolio application built to showcase a developer profile in a clean and beginner-friendly way.

## Project Overview

The app presents:

- a profile section with the developer name and role
- a projects section with interactive buttons
- a social media section with icons and external links
- a polished single-page portfolio layout

The main goal of this project is to help beginners understand how a Flutter UI is structured using widgets and how a simple mobile app can be built step by step.

## Architecture

This project uses a simple three-layer Flutter architecture:

1. Presentation Layer
   - `main.dart` contains the UI for the portfolio page.
   - `PortfolioHomePage` renders the profile, projects, social links, and feedback form.
   - Material widgets such as `Scaffold`, `AppBar`, `Card`, `Form`, and `ListTile` are used to build the screen.

2. State and Interaction Layer
   - The page is a `StatefulWidget`, so it can manage form input, selection state, loading status, and feedback list updates.
   - User actions such as submitting feedback, editing a saved item, or deleting a saved item trigger state updates.

3. Data Layer
   - Feedback data is sent to Supabase using the service layer in `lib/services/feedback_service.dart`.
   - The app connects to Supabase through `lib/config/supabase_config.dart`.
   - The `feedback` table stores the submitted records and returns them to the UI for display.

### Application Flow

1. The user opens the portfolio page.
2. The app loads the existing feedback from Supabase.
3. The user fills the feedback form and submits it.
4. The form data is inserted into the `feedback` table.
5. The UI refreshes and shows the latest feedback entries.
6. Users can edit or delete records directly from the list.

## File Structure

- `lib/main.dart` — contains the complete app UI and layout logic
- `assets/profile.png` — local profile image used in the app
- `test/widget_test.dart` — checks that the app renders the expected sections

## Why This Project Is Beginner Friendly

- The code is written in a simple and readable way.
- The UI is built using standard Flutter widgets.
- The project uses only basic state management for interactive project buttons.
- There is no backend or database dependency, making it easy to learn and modify.

## How to Run

Use the following commands:

```bash
flutter pub get
flutter run
```

## Feedback Backend Setup

To make the feedback form save data to Supabase, create a table named `feedback` in your Supabase project.

### SQL table

```sql
create table public.feedback (
  id uuid primary key default gen_random_uuid(),
  name text not null,
  phone text not null,
  description text not null,
  created_at timestamp with time zone default now()
);
```

### Runtime configuration

Set these values before running the app:

```bash
flutter run --dart-define=SUPABASE_URL=your-project-url --dart-define=SUPABASE_ANON_KEY=your-anon-key
```
flutter run --dart-define=SUPABASE_URL=https://ochajhysuwyixtkvymno.supabase.co --dart-define=SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Im9jaGFqaHlzdXd5aXh0a3Z5bW5vIiwicm9sZSI6ImFub24iLCJpYXQiOjE3ODUwMzYzMjYsImV4cCI6MjEwMDYxMjMyNn0.06O_O5C4rfherz054wCU-RE4li79bjGKaO9wuOBsbks

If you prefer, you can also set them in your environment before launching the app.

## Future Improvements

This app can be expanded later with:

- your real profile image and personal details
- actual social media URLs
- dark mode support
- separate pages for each project
- animations and a more advanced design
