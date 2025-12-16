# Job Portal

A full-stack job portal application that connects job seekers with employers. Built with React, Node.js, Express, and MongoDB.

## Features

### For Job Seekers

- Browse and search jobs by title and location
- Apply for jobs with resume upload
- Track application status
- User authentication via Clerk
- Update profile and resume

### For Recruiters/Companies

- Company registration and login
- Post and manage job listings
- View job applications
- Update application status
- Toggle job visibility
- Dashboard for managing recruitment

## Tech Stack

### Frontend

- **React** 18.3.1 - UI library
- **Vite** - Build tool and dev server
- **React Router** - Client-side routing
- **Clerk** - Authentication and user management
- **Axios** - HTTP client
- **Tailwind CSS** - Styling
- **Quill** - Rich text editor
- **React Toastify** - Notifications
- **Moment.js** - Date formatting

### Backend

- **Node.js** with **Express** - Server framework
- **MongoDB** with **Mongoose** - Database
- **Clerk Express** - Backend authentication
- **Cloudinary** - Image and file storage
- **Multer** - File upload handling
- **JWT** - Token generation
- **bcrypt** - Password hashing
- **Sentry** - Error monitoring
- **Svix** - Webhook handling

## Project Structure

```
job-portal/
├── client/                 # Frontend React application
│   ├── src/
│   │   ├── assets/        # Static assets
│   │   ├── components/    # React components
│   │   ├── context/       # Context API
│   │   ├── pages/         # Page components
│   │   ├── App.jsx        # Main app component
│   │   └── main.jsx       # Entry point
│   └── package.json
│
└── server/                # Backend Node.js application
    ├── config/            # Configuration files
    ├── controllers/       # Route controllers
    ├── middleware/        # Custom middleware
    ├── models/            # Mongoose models
    ├── routes/            # API routes
    ├── utils/             # Utility functions
    └── server.js          # Server entry point
```

## Data Models

### User

- Clerk-managed authentication
- Profile with name, email, image
- Resume storage

### Company

- Name, email, password
- Company image
- JWT-based authentication

### Job

- Title, description, location
- Category, level, salary
- Visibility toggle
- Associated with company

### JobApplication

- Links user, company, and job
- Application status (Pending/Accepted/Rejected)
- Timestamp

## API Routes

### Jobs (`/api/jobs`)

- `GET /` - Get all jobs
- `GET /:id` - Get job by ID

### Company (`/api/company`)

- `POST /register` - Register company
- `POST /login` - Company login
- `GET /company` - Get company data (protected)
- `POST /post-job` - Post a job (protected)
- `GET /applicants` - Get job applicants (protected)
- `GET /list-jobs` - Get company's posted jobs (protected)
- `POST /change-status` - Update application status (protected)
- `POST /change-visiblity` - Toggle job visibility (protected)

### Users (`/api/users`)

- `GET /user` - Get user data
- `POST /apply` - Apply for a job
- `GET /applications` - Get user's applications
- `POST /update-resume` - Update user resume

### Webhooks

- `POST /webhooks` - Clerk user synchronization

## Setup and Installation

### Prerequisites

- Node.js (v14 or higher)
- MongoDB
- Cloudinary account
- Clerk account

### Environment Variables

#### Server (`.env`)

```env
MONGODB_URI=your_mongodb_connection_string
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_SECRET_KEY=your_cloudinary_secret_key
CLERK_WEBHOOK_SECRET=your_clerk_webhook_secret
JWT_SECRET=your_jwt_secret
SENTRY_DSN=your_sentry_dsn (optional)
PORT=5010
```

#### Client (`.env`)

```env
VITE_BACKEND_URL=http://localhost:5010
VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
```

### Installation Steps

1. **Clone the repository**

```bash
git clone <repository-url>
cd job-portal
```

2. **Install server dependencies**

```bash
cd server
npm install
```

3. **Install client dependencies**

```bash
cd client
npm install
```

4. **Set up environment variables**

- Create `.env` files in both `server` and `client` directories
- Add the required environment variables

5. **Run the application**

Start the backend server:

```bash
cd server
npm run server
```

Start the frontend development server:

```bash
cd client
npm run dev
```

The application will be available at:

- Frontend: `http://localhost:5173` (or the port Vite assigns)
- Backend: `http://localhost:5010`

## Available Scripts

### Client

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

### Server

- `npm run server` - Start with nodemon (development)
- `npm start` - Start production server

## Deployment

This application is deployed on Vercel with separate deployments for frontend and backend.

### Live Application

- **Frontend**: [https://job-portal-fullstack-client-rho.vercel.app/](https://job-portal-fullstack-client-rho.vercel.app/)
- **Backend API**: [https://job-portal-fullstack-server-ashen.vercel.app/](https://job-portal-fullstack-server-ashen.vercel.app/)

### Deployment Configuration

Both client and server include `vercel.json` configuration files for seamless deployment on Vercel.

#### Backend Deployment

1. Push your code to a Git repository (GitHub, GitLab, or Bitbucket)
2. Import the project to Vercel
3. Set the root directory to `server`
4. Add all required environment variables in Vercel project settings
5. Deploy

#### Frontend Deployment

1. Import the project to Vercel
2. Set the root directory to `client`
3. Add environment variables:
   - `VITE_BACKEND_URL` - Set to your deployed backend URL
   - `VITE_CLERK_PUBLISHABLE_KEY` - Your Clerk publishable key
4. Deploy

**Note**: Make sure to update the `VITE_BACKEND_URL` in your frontend environment variables to point to the deployed backend URL.

## Features in Detail

### Authentication

- **Job Seekers**: Clerk-based authentication with OAuth support
- **Recruiters**: Custom JWT-based authentication with bcrypt password hashing

### File Management

- Resume uploads for job seekers
- Company logo uploads
- Integration with Cloudinary for file storage

### Error Monitoring

- Sentry integration for tracking and debugging errors in production

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a pull request

## License

ISC
