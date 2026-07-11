# PassOp - Secure Full-Stack Password Manager

**Live Demo:** [https://passop-frontend-seven.vercel.app](https://passop-frontend-seven.vercel.app/)

PassOp is a full-stack password management application built using the MERN stack. It allows users to securely store, manage, and retrieve their passwords for various websites. The project was built with a strong focus on data security, utilizing session-based authentication and database-level encryption.

## 🚀 Features

* **Secure Authentication:** User accounts are protected using `bcrypt` hashing for login credentials.
* **Session Management:** Implements secure, persistent user sessions stored in MongoDB using HTTP-only cookies, preventing XSS attacks.
* **Data Encryption:** All user passwords saved in the vault are encrypted using **AES encryption** before being stored in the database, ensuring that even with database access, plain text passwords cannot be read.
* **CRUD Operations:** Users can easily add, view, edit, and delete their saved passwords.
* **Global State:** Uses React's Context API to manage user authentication state cleanly across the application without prop-drilling.
* **Responsive UI:** Fully responsive frontend built with React and Tailwind CSS.
* **Real-time Feedback:** Integrated toast notifications to provide instant feedback on user actions (success/error states).

## 🛠️ Tech Stack

**Frontend:**
* React.js
* Tailwind CSS
* Context API (State Management)
* Deployed on: **Vercel**

**Backend:**
* Node.js
* Express.js
* `express-session` & `connect-mongodb-session` (Auth)
* `crypto` module (AES Encryption)
* Deployed on: **Render**

**Database:**
* MongoDB Atlas

## 🔒 Security Architecture

Unlike basic CRUD apps, PassOp does not store raw passwords in the database. 
1. When a user creates an account, their master password is hashed via `bcrypt`.
2. When a user saves a new password for a website, the backend intercepts the request, encrypts the password using a cryptographic algorithm, and saves the ciphertext to MongoDB.
3. When the user requests their vault, the backend decrypts the passwords before sending them securely to the frontend.

## 💻 Local Development Setup

To run this project locally, you will need Node.js and a MongoDB database (local or Atlas).

### 1. Clone the repository
```bash
git clone https://github.com/MRIDUL1978/MERN-PROJECTS.git
cd MERN-PROJECTS
```

### 2. Backend Setup
```bash
cd Backend
npm install
```

Create a .env file in the Backend directory and add the following variables:
```bash
# Your MongoDB connection string (Make sure to specify the DB name, e.g., /PassOp)
DB_PATH=mongodb+srv://<username>:<password>@cluster.mongodb.net/PassOp?appName=Cluster0
# Secret key for session signing and encryption
SECRET_KEY=your_super_secret_key_here
# Port for the local server
PORT=10000
# URL of your local frontend
FRONTEND_URL=http://localhost:5173
```

Start the backend server:
```bash
node server.js
```

### 3. Frontent Setup
Open a new terminal window:
```bash
cd Frontend
npm install
```

Create a .env file in the Frontend directory:
```bash
# URL of your local backend
VITE_API_URL=http://localhost:10000
```

Start the React development server:
```bash
npm run dev
```

🌐 Deployment Note
If deploying this project, ensure that:

1. Your backend CORS configuration allows your exact production frontend URL.

2. The FRONTEND_URL environment variable on your backend matches the deployed frontend URL without a trailing slash.

3. A vercel.json file is included in the frontend to handle React Router page refreshes correctly.

## 👨‍💻 Author
Mridul Shaily
GitHub: @MRIDUL1978
