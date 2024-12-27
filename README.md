# Job Jotter

Job Jotter is a web application designed to help users organize and track their job applications, interviews, and reminders. The platform provides a user-friendly interface for managing job-seeking activities efficiently.

## Production URL

[Job Jotter Production](https://jobjotter.onrender.com)

## Features

1. **Sign Up/Login**: Secure account creation and authentication using JSON Web Tokens (JWT).
2. **Dashboard**: Overview of all job applications, interview schedules, and reminders.
3. **Add Job Application**: Form to input job details or import information using third-party APIs.
4. **Track Progress**: Update application statuses and add detailed notes.
5. **Set Reminders**: Schedule follow-ups and interviews with Google Calendar integration.
6. **Logout**: Securely end sessions.

## Tech Stack

- **Front-End**: React (with Vite for development)
- **Back-End**: Node.js with Express
- **Database**: PostgreSQL
- **Styling**: Bootstrap
- **Authentication**: JWT with bcrypt for password hashing

## Updated Database Schema

### Users Table
| Column      | Type     | Description                     |
|-------------|----------|---------------------------------|
| id          | SERIAL   | Primary Key                    |
| username    | TEXT     | Unique, required               |
| password    | TEXT     | Hashed, required               |
| email       | TEXT     | Unique, required               |
| google_access_token      | TEXT     | Additional Information             |
| google_refresh_token       | TEXT     | Additional Information               |
| google_token_expiry      | TEXT     | Additional Information               |

### Applications Table
| Column      | Type       | Description                     |
|-------------|------------|---------------------------------|
| id          | SERIAL     | Primary Key                    |
| user_id     | INTEGER    | Foreign Key referencing Users  |
| company     | TEXT       | Required                       |
| job_title   | TEXT       | Required                       |
| status      | TEXT       | Status of application          |
| date_applied| DATE       | Date application was submitted |
| notes       | TEXT       | Additional information         |

### Interviews Table
| Column      | Type       | Description                     |
|-------------|------------|---------------------------------|
| id          | SERIAL     | Primary Key                    |
| application_id | INTEGER | Foreign Key referencing Applications |
| date        | DATE       | Interview date                 |
| time        | TIME       | Interview time                 |
| location    | TEXT       | Interview location             |
| notes       | TEXT       | Additional information         |

### Reminders Table
| Column      | Type       | Description                     |
|-------------|------------|---------------------------------|
| id          | SERIAL     | Primary Key                    |
| user_id     | INTEGER    | Foreign Key referencing Users  |
| reminder_type | TEXT     | Type of reminder (e.g., follow-up, interview) |
| date        | DATE       | Reminder date                  |
| description | TEXT       | Additional details             |

## Security Measures

1. **Password Security**: All passwords are hashed using bcrypt.
2. **Authentication**: JWT stored securely in HTTP-only cookies.
3. **Environment Variables**: Sensitive information is stored in a `.env` file.

## Integrations

- **Google Calendar API**: Enables scheduling reminders and interviews directly on the user’s calendar.

## Deployment

The application is hosted on [Render](https://render.com). The production URL is available above.

## Installation and Setup

### Prerequisites

- Node.js (v20.16.0 recommended)
- PostgreSQL

### Steps

1. Clone the repository.
   ```bash
   git clone https://github.com/DonjVS/job-jotter.git
   cd job-jotter
   ```

2. Install dependencies.
   ```bash
   npm install
   ```

3. Set up the database:
   - Create a PostgreSQL database.
   - Run the provided schema and seed files.

4. Create a `.env` file with the following variables:
   ```env
   DATABASE_URL=<your-database-url>
   SECRET_KEY=<your-jwt-secret>
   GOOGLE_CALENDAR_CLIENT_ID=<google-client-id>
   GOOGLE_CALENDAR_CLIENT_SECRET=<google-client-secret>
   GOOGLE_CALENDAR_REDIRECT_URI=<redirect-uri>
   ```

5. Start the server:
   ```bash
   npm start
   ```

6. Navigate to the front-end client folder and start the React application:
   ```bash
   npm run dev
   ```

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request.
