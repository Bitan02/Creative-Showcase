# Creative Showcase

An Instagram-like image sharing web application built with the MERN stack. Share your art and preserve your memories.

## Tech Stack

### Frontend
- React (JavaScript)
- Tailwind CSS
- React Router
- Axios

### Backend
- Node.js
- Express.js
- MongoDB with Mongoose
- JWT Authentication
- bcrypt for password hashing
- Multer + Cloudinary for image uploads

## Features

- User authentication (register, login)
- Secure JWT-based authentication
- Image upload with Cloudinary integration
- Global feed showing all users' images
- User profiles (public and private)
- Search users by username
- Delete own images
- Responsive, modern UI

## Prerequisites

- Node.js (v16 or higher)
- MongoDB (local or MongoDB Atlas)
- Cloudinary account (for image storage)
- npm or yarn

## Setup Instructions

### 1. Clone the repository

```bash
git clone <repository-url>
cd artist-image-vault
```

### 2. Backend Setup

Navigate to the server directory:

```bash
cd server
```

Install dependencies:

```bash
npm install
```

Create a `.env` file in the `server` directory:

```env
MONGO_URI=mongodb://localhost:27017/creative-showcase
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
CLOUDINARY_CLOUD_NAME=your-cloudinary-cloud-name
CLOUDINARY_API_KEY=your-cloudinary-api-key
CLOUDINARY_API_SECRET=your-cloudinary-api-secret
PORT=5000
```

**Important:** Replace the placeholder values:
- `MONGO_URI`: Your MongoDB connection string (use MongoDB Atlas connection string if using cloud)
- `JWT_SECRET`: A random secret string for JWT token signing
- `CLOUDINARY_CLOUD_NAME`, `CLOUDINARY_API_KEY`, `CLOUDINARY_API_SECRET`: Get these from your Cloudinary dashboard

### 3. Frontend Setup

Navigate to the client directory:

```bash
cd ../client
```

Install dependencies:

```bash
npm install
```

(Optional) Create a `.env` file in the `client` directory if you want to customize the API URL:

```env
VITE_API_URL=http://localhost:5000/api
```

### 4. Running the Application

#### Start the Backend Server

From the `server` directory:

```bash
npm start
```

For development with auto-reload:

```bash
npm run dev
```

The server will run on `http://localhost:5000`

#### Start the Frontend Development Server

From the `client` directory:

```bash
npm run dev
```

The frontend will run on `http://localhost:3000`

## Project Structure

```
root/
├── client/
│   ├── src/
│   │   ├── components/      # Reusable React components
│   │   ├── pages/           # Page components
│   │   ├── context/         # React context (AuthContext)
│   │   ├── services/        # API service functions
│   │   ├── App.jsx          # Main App component
│   │   └── main.jsx         # Entry point
│   ├── index.html
│   └── package.json
│
└── server/
    ├── config/              # Configuration files (Cloudinary)
    ├── controllers/         # Route controllers
    ├── models/              # Mongoose models
    ├── routes/              # Express routes
    ├── middleware/         # Custom middleware (auth, upload)
    ├── server.js            # Express server entry point
    └── package.json
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user

### Users
- `GET /api/users/me` - Get current user profile (protected)
- `GET /api/users/search?username=` - Search users by username (protected)
- `GET /api/users/:username` - Get public user profile

### Posts
- `POST /api/posts/upload` - Upload image (protected)
- `GET /api/posts/feed` - Get global feed (protected)
- `GET /api/posts/user/:username` - Get posts by username
- `DELETE /api/posts/:postId` - Delete post (protected, owner only)

## Usage

1. **Sign Up**: Create a new account with username, email, and password
2. **Login**: Sign in with your email and password
3. **Upload Images**: Go to your profile page (`/me`) and click "Choose Image" to upload
4. **View Feed**: Visit the Dashboard to see all users' images
5. **Search Users**: Use the search bar in the navbar to find users by username
6. **View Profiles**: Click on any username to view their public profile
7. **Delete Images**: On your profile page, hover over your images and click "Delete"

## Environment Variables

### Server (.env)
- `MONGO_URI` - MongoDB connection string
- `JWT_SECRET` - Secret key for JWT token signing
- `CLOUDINARY_CLOUD_NAME` - Your Cloudinary cloud name
- `CLOUDINARY_API_KEY` - Your Cloudinary API key
- `CLOUDINARY_API_SECRET` - Your Cloudinary API secret
- `PORT` - Server port (default: 5000)

### Client (.env) - Optional
- `VITE_API_URL` - Backend API URL (default: http://localhost:5000/api)

## Notes

- Images are stored on Cloudinary, not locally
- JWT tokens are stored in localStorage
- Passwords are hashed using bcrypt
- The app uses ES6 modules (type: "module" in package.json)
- Frontend uses Vite as the build tool

## Troubleshooting

1. **MongoDB Connection Error**: Make sure MongoDB is running and the connection string is correct
2. **Cloudinary Upload Fails**: Verify your Cloudinary credentials in the `.env` file
3. **CORS Errors**: The backend has CORS enabled, but make sure the frontend is making requests to the correct URL
4. **JWT Token Errors**: Ensure `JWT_SECRET` is set in the server `.env` file

## License

ISC

