Frontend Application
This is a React-based frontend application developed as part of a MERN (MongoDB, Express.js, React, Node.js) stack project. The application integrates modern web development technologies to deliver a responsive and interactive user interface.
Features
React 19 – Latest version of React with concurrent rendering capabilities
React Router – Client-side routing for seamless navigation
Google OAuth – Secure user authentication through Google accounts
Axios – HTTP client for API communication
JWT Authentication – Token-based user authentication and authorization
React Icons – Icon library for user interface enhancement
React Window – Optimized rendering for large data lists
Testing – Jest and React Testing Library for unit and integration tests
Prerequisites
Node.js (version 14 or higher)
npm (version 6 or higher) or Yarn
Getting Started
1.	Clone the repository
git clone <repository-url>
cd miniproject/frontend
2.	Install dependencies
npm install
or
yarn install
3.	Environment Setup
Create a .env file in the root directory and define the following variables:
REACT_APP_API_URL=http://localhost:5000
REACT_APP_GOOGLE_CLIENT_ID=your-google-client-id
4.	Start the development server
npm start
or
yarn start
The application will be available at http://localhost:3000
Project Structure
src/
├── components/ (Reusable UI components)
├── pages/ (Page-level components)
├── assets/ (Static assets such as images, fonts, etc.)
├── context/ (React context providers)
├── hooks/ (Custom React hooks)
├── services/ (API and data services)
├── styles/ (Global styles and themes)
└── utils/ (Helper functions and constants)
Testing
To run the test suite:
npm test
or
yarn test
Build for Production
npm run build
or
yarn build
This creates an optimized production build in the “build” directory.
Contributing
1.	Fork the repository
2.	Create a feature branch (git checkout -b feature/YourFeature)
3.	Commit changes (git commit -m 'Add YourFeature')
4.	Push the branch (git push origin feature/YourFeature)
5.	Open a Pull Request
License
This project is licensed under the MIT License. Refer to the LICENSE file for details.
Acknowledgments
Create React App
React Community
All contributors and maintainers
________________________________________
Backend Server
The backend server is built using Node.js, Express.js, and MongoDB. It provides RESTful API endpoints for the frontend and integrates with Google’s Generative AI services for intelligent evaluation features.
Features
Express.js – Lightweight web framework for building APIs
MongoDB with Mongoose – Schema-based data modeling and validation
JWT Authentication – Secure authentication using JSON Web Tokens
CORS – Cross-Origin Resource Sharing configuration
Environment Variables – Secure configuration using dotenv
Google Generative AI – Integration with Gemini AI models
Cookie Parser – Middleware for parsing HTTP cookies
RESTful API – Modular and structured API design
Prerequisites
Node.js (version 14 or higher)
npm (version 6 or higher) or Yarn
MongoDB (local or cloud instance)
Google Cloud account with access to Generative AI API
Getting Started
1.	Clone the repository
git clone <repository-url>
cd miniproject/backend
2.	Install dependencies
npm install
or
yarn install
3.	Environment Setup
Create a .env.local file in the root directory and define the following:
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
CLIENT_URL=http://localhost:3000
GOOGLE_API_KEY=your_google_ai_api_key
4.	Start the development server
node server.js
or
npx nodemon server.js
The server will be available at http://localhost:5000
Project Structure
backend/
├── routes/
│ ├── auth.js (Authentication routes)
│ ├── dash.js (Dashboard routes)
│ └── admin_routes.js (Admin management routes)
├── models/ (Database schemas)
├── middleware/ (Authentication and validation middleware)
├── config/ (Configuration files)
├── utils/ (Helper functions)
├── server.js (Main application file)
└── package.json (Project dependencies)
API Endpoints
Authentication
POST /api/auth/register – Register a new user
POST /api/auth/login – Authenticate user
GET /api/auth/logout – Logout and clear session
GET /api/auth/me – Retrieve logged-in user profile
Dashboard
GET /api/dashboard – Fetch dashboard data
POST /api/interview – Initiate a new interview
GET /api/interview/:id – Retrieve interview details
Admin
GET /api/admin/users – Retrieve all registered users
PUT /api/admin/users/:id – Modify user role or access
Authentication
JWT tokens are used for session management.
Include the token in the request header for accessing protected routes:
Authorization: Bearer <your_jwt_token>
CORS Configuration
CORS is restricted to requests originating from the URL defined in the CLIENT_URL environment variable.
Database
The backend uses MongoDB with Mongoose ODM. Update the MONGODB_URI in .env.local with the appropriate connection string before running the server.
Testing
To execute backend tests (if implemented):
npm test
or
yarn test
Deployment
1.	Build the application
npm run build
2.	Start the production server
NODE_ENV=production node server.js
Contributing
1.	Fork the repository
2.	Create a feature branch (git checkout -b feature/YourFeature)
3.	Commit changes (git commit -m 'Add YourFeature')
4.	Push the branch (git push origin feature/YourFeature)
5.	Submit a Pull Request
