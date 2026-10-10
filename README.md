# Mini Ticket Tracker

A full-stack mini ticket tracker built with Laravel REST API, Next.js, MySQL, and Tailwind CSS.

## Setup and Run Instructions

### Prerequisites
- PHP 8.3+
- Composer
- Node.js 20+
- MySQL
- npm

### Backend Setup

1. Navigate to the backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
composer install
```

3. Copy environment file and configure:
```bash
cp .env.example .env
php artisan key:generate
```

4. Configure your database in `.env`:
```
DB_DATABASE=mini-ticket-tracker
DB_USERNAME=your_username
DB_PASSWORD=your_password
```

5. Run migrations:
```bash
php artisan migrate
```

6. Start the Laravel server:
```bash
php artisan serve
```
The API will be available at `http://localhost:8000`

### Frontend Setup

1. Navigate to the frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Create environment file:
```bash
cp .env.example .env
```

The default `NEXT_PUBLIC_API_URL` is set to `http://localhost:8000`. Adjust if your backend runs on a different port.

4. Start the development server:
```bash
npm run dev
```
The frontend will be available at `http://localhost:3000`

### Running Tests

Backend tests:
```bash
cd backend
php artisan test
```

Frontend linting:
```bash
cd frontend
npm run lint
```

Frontend build:
```bash
cd frontend
npm run build
```

## Decisions & Tradeoffs

The implementation prioritizes simplicity and functionality over feature completeness. I chose Laravel for the backend due to its robust ORM and built-in validation, which allowed rapid development of the required endpoints. For the frontend, Next.js with TypeScript provided type safety and modern React patterns without introducing additional state management libraries like Redux or React Query, keeping the implementation lightweight. The UI uses Tailwind CSS for consistent styling without custom CSS files. I implemented client-side state management with React hooks rather than server components for interactivity, which adds complexity but provides real-time updates. CORS was configured permissively for local development; in production, this should be restricted to specific origins. The pagination uses the backend's built-in Laravel paginator rather than client-side pagination to handle large datasets efficiently. Status updates use a compact select control for quick changes rather than a separate edit form, prioritizing usability. The create ticket form is a modal to maintain context while adding new tickets. No authentication or authorization was implemented as it was outside the assignment scope. The statistics are fetched from the API on every update rather than cached, which is simple but could be optimized for high-traffic scenarios.
