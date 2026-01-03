# Splity Backend

Splity is a backend service for a group expense sharing application. It allows users to create groups, add expenses, and settle debts, automatically calculating net balances for each group member.

## Features

- **User Authentication**: Secure registration and login using JWT.
- **Group Management**: Create groups and add members.
- **Expense Tracking**: Add expenses with equal or unequal splits.
- **Balance Calculation**: Automatically updates net balances for all group members.
- **Settlements**: Record payments to settle debts between members.
- **Expense Categories**: Categorize expenses (Food, Transport, etc.).
- **Activity Logs**: Track important events like group creation and expense additions.
- **Robustness**: 
    - Atomic balance updates for concurrency safety.
    - Stronger security with strict validation and password strength checks.
    - Centralized error handling.

## Tech Stack

- **Node.js**: Runtime environment.
- **Express.js**: Web framework.
- **MongoDB**: NoSQL database.
- **Mongoose**: ODM for MongoDB.
- **JWT**: Authentication.

## Prerequisites

- Node.js (v14 or higher)
- MongoDB (running locally or cloud instance)

## Installation

1. Clone the repository.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create a `.env` file in the root directory with the following variables:
   ```env
   PORT=5000
   MONGO_URI=mongodb://localhost:27017/splity
   JWT_SECRET=your_jwt_secret
   ```

## Usage

1. Start the server:
   ```bash
   npm start
   ```
2. The API will be available at `http://localhost:5000`.

## API Endpoints

### Auth
- `POST /api/auth/register`: Register a new user.
- `POST /api/auth/login`: Login user.
- `GET /api/auth/me`: Get current user profile.

### Groups
- `POST /api/groups`: Create a new group.
- `GET /api/groups`: Get user's groups.
- `GET /api/groups/:id`: Get group details.
- `POST /api/groups/:id/members`: Add a member to a group.

### Expenses
- `POST /api/expenses`: Add an expense (supports `category`).
- `GET /api/expenses/:groupId`: Get expenses for a group.

### Settlements
- `POST /api/settlements`: Record a settlement.
- `GET /api/settlements/:groupId`: Get settlements for a group.

### Activity
- `GET /api/activity`: Get recent activity logs for the user.
