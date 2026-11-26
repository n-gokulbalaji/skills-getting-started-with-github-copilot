# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Sign up for activities and remove participants

## Getting Started

From the repository root:

1. Install the dependencies:

   ```
   python -m pip install -r requirements.txt
   ```

2. Start the application:

   ```
   python -m uvicorn src.app:app --reload
   ```

3. Open the website at http://127.0.0.1:8000. You can also visit:
   - API documentation: http://127.0.0.1:8000/docs
   - Alternative documentation: http://127.0.0.1:8000/redoc

## Verify the Website

1. Confirm the activities load on the home page.
2. Enter a student email, choose an activity, and select **Sign Up**.
3. Confirm a success message appears and the participant list updates without a refresh.
4. Use the remove button beside a participant and confirm the list updates.

The signup data is held in memory and resets when the server restarts.

## Run Backend Tests

From the repository root, run:

```
python -m pytest
```

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up for an activity                                             |
| DELETE | `/activities/{activity_name}/signup?email=student@mergington.edu` | Unregister from an activity                                         |

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.
