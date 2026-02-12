# Digital Healthcare System - Complete Setup Guide

## Project Overview

This is a comprehensive **Digital Healthcare System** that connects patients and doctors in a secure, digital-first environment. The system manages health records, medications, vaccinations, and includes an AI-powered health assistant with QR code integration.

### Key Features:
✅ Patient registration with unique Health IDs
✅ Medication and vaccination tracking
✅ QR code generation and scanning
✅ Health AI chatbot (real-time)
✅ Doctor patient management portal
✅ Secure authentication with JWT
✅ Responsive design for all devices
✅ Complete animation and modern UI

---

## Quick Start (5 minutes)

### Prerequisites
- **Node.js** v14+ ([Download](https://nodejs.org))
- **MongoDB** ([Local](https://docs.mongodb.com/manual/installation/) or [Atlas Cloud](https://www.mongodb.com/cloud/atlas))
- **Git** (optional)

### One-Click Start (Windows)

Simply double-click the `run_app.bat` file in the project root.

This script will automatically:
1. Install all dependencies (if missing)
2. Configure the `.env` file
3. Start both Backend and Frontend servers

**Alternative (Command Line):**
```cmd
run_app.bat
```

### Step 1: Clone/Extract Project
```bash
cd d:\new\pro
```

### Step 2: Setup Backend

```bash
# Navigate to backend
cd backend

# Install dependencies
npm install

# Configure environment
# Edit .env file with your MongoDB connection string
# Default: MONGODB_URI=mongodb://localhost:27017/digital-healthcare

# Start server
npm run dev
```

✅ Backend running on `http://localhost:5000`

### Step 3: Setup Frontend

```bash
# In new terminal, navigate to frontend
cd frontend

# Install dependencies
npm install

# Start development server
npm start
```

✅ Frontend running on `http://localhost:3000`

---

## Detailed Setup Instructions

### Prerequisites Installation

#### Windows:

**Node.js:**
1. Download from [nodejs.org](https://nodejs.org)
2. Run installer
3. Verify: `node -v` and `npm -v`

**MongoDB (Local):**
1. Download from [mongodb.com](https://www.mongodb.com/try/download/community)
2. Run installer
3. Start MongoDB:
   ```bash
   mongod
   ```

**Alternative - MongoDB Atlas (Cloud):**
1. Go to [mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
2. Create free account
3. Create cluster
4. Get connection string
5. Update in `.env`: `MONGODB_URI=your_connection_string`

---

### Backend Installation

#### 1. Navigate to Backend
```bash
cd d:\new\pro\backend
```

#### 2. Install Dependencies
```bash
npm install
```

This installs:
- Express.js - Web framework
- Mongoose - MongoDB ODM
- bcryptjs - Password hashing
- jsonwebtoken - Authentication
- socket.io - Real-time chat
- And more...

#### 3. Configure Environment
```bash
# Copy example env file
cp .env.example .env

# Edit .env file with your settings
```

**Environment Variables:**
```env
MONGODB_URI=mongodb://localhost:27017/digital-healthcare
PORT=5000
JWT_SECRET=your-secret-key-123
NODE_ENV=development
```

#### 4. Start Backend Server

**Development (with auto-reload):**
```bash
npm run dev
```

**Production:**
```bash
npm start
```

Expected output:
```
Server running on port 5000
MongoDB connected
```

#### 5. Test Backend
Open browser: `http://localhost:5000`

Or test API:
```bash
curl http://localhost:5000/api/patients
```

---

### Frontend Installation

#### 1. Navigate to Frontend
```bash
cd d:\new\pro\frontend
```

#### 2. Install Dependencies
```bash
npm install
```

This installs:
- React 18 - UI framework
- React Router - Navigation
- Axios - HTTP client
- Socket.io Client - Real-time messaging
- And more...

#### 3. Configure API Endpoint (if needed)

Edit `package.json`:
```json
"proxy": "http://localhost:5000"
```

#### 4. Start Frontend

```bash
npm start
```

This will:
- Start development server
- Open browser automatically at `http://localhost:3000`
- Enable hot reload on file changes

---

## Using the Application

### Patient Portal

#### 1. Create Account
1. Go to `http://localhost:3000`
2. Click "Patient" tab
3. Click "Create Account"
4. Fill in:
   - **Name**: Your full name
   - **Email**: your.email@example.com
   - **Password**: At least 6 characters
   - **Confirm Password**: Repeat password
5. Click "Create Account"
6. Receive unique **Health ID** (e.g., health0001)

#### 2. Patient Dashboard
After login, you have access to:

**📋 Medications**
- View medications prescribed
- See dosage and schedule
- View medication history

**💉 Vaccinations**
- Track vaccination status
- See completed vaccinations
- View upcoming appointments

**📱 QR Code**
- View your personal QR code
- Share with healthcare providers
- Contains all your health info

**🤖 Health AI**
- Ask health questions
- Get instant AI responses
- Browse health tips

**❓ Help**
- Get feature information
- Learn about privacy
- Find support contact

### Doctor Portal

#### 1. Login
1. Go to `http://localhost:3000`
2. Click "Doctor" tab
3. Auto-filled credentials:
   - **Email**: doctor@gmail.com
   - **Password**: health123
4. Click "Doctor Login"

#### 2. Find Patient
1. Enter patient's **Health ID** (e.g., health0001)
2. Click "Search"
3. View patient details

#### 3. Update Patient Records

**Add Medications:**
1. Click "Medications" tab
2. Fill in tablet details
3. Add schedule (multiple days)
4. Click "Submit"

**Add Vaccinations:**
1. Click "Vaccinations" tab
2. Enter vaccination details
3. Schedule future vaccinations
4. Click "Submit"

**Scan QR Code:**
1. Click "Scanner" tab
2. Upload patient's QR code image
3. View decoded patient information

---

## Project File Structure

```
project/
│
├── backend/
│   ├── models/
│   │   ├── Patient.js          # Patient data model
│   │   ├── Tablet.js           # Medication model
│   │   ├── Vaccination.js      # Vaccination model
│   │   ├── QRCode.js           # QR code model
│   │   └── Doctor.js           # Doctor credentials
│   │
│   ├── controllers/
│   │   ├── authController.js   # Login/Register logic
│   │   ├── patientController.js # Patient operations
│   │   └── doctorController.js  # Doctor operations
│   │
│   ├── routes/
│   │   ├── auth.js             # Auth endpoints
│   │   ├── patients.js         # Patient endpoints
│   │   ├── doctors.js          # Doctor endpoints
│   │   └── healthRecords.js    # Health data endpoints
│   │
│   ├── middleware/
│   │   └── auth.js             # JWT verification
│   │
│   ├── server.js               # Main server file
│   ├── package.json            # Dependencies
│   ├── .env.example            # Environment template
│   └── README.md               # Backend docs
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── TabletModule.js         # Medication display
│   │   │   ├── VaccinationModule.js    # Vaccination tracking
│   │   │   ├── AIChat.js               # AI chatbot
│   │   │   ├── QRScanner.js            # QR scanning
│   │   │   ├── HelpModal.js            # Help information
│   │   │   ├── AddTabletForm.js        # Medication form
│   │   │   └── AddVaccinationForm.js   # Vaccination form
│   │   │
│   │   ├── pages/
│   │   │   ├── LoginPage.js            # Authentication
│   │   │   ├── PatientDashboard.js     # Patient main page
│   │   │   └── DoctorDashboard.js      # Doctor main page
│   │   │
│   │   ├── utils/
│   │   │   ├── api.js                  # API client
│   │   │   ├── helpers.js              # Utility functions
│   │   │   └── auth.js                 # Auth utilities
│   │   │
│   │   ├── App.js                      # Main component
│   │   └── index.js                    # Entry point
│   │
│   ├── public/
│   │   └── index.html                  # HTML template
│   │
│   ├── package.json                    # Dependencies
│   └── README.md                       # Frontend docs
│
├── README.md                           # Main documentation
├── SETUP_GUIDE.md                      # This file
└── .gitignore                          # Git ignore rules
```

---

## Database Setup

### MongoDB Local Setup

#### Windows:

1. **Install MongoDB Community:**
   - Download from [mongodb.com](https://www.mongodb.com/try/download/community)
   - Run installer
   - Select "Install MongoDB as a Service" (recommended)

2. **Start MongoDB:**
   ```bash
   mongod
   ```
   Or if installed as service, it starts automatically

3. **Verify Connection:**
   ```bash
   mongo
   ```

### MongoDB Atlas (Cloud) Setup

1. **Create Account:**
   - Go to [mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
   - Sign up (free tier available)

2. **Create Cluster:**
   - Click "Create Cluster"
   - Select free tier
   - Choose region
   - Click "Create Cluster"

3. **Get Connection String:**
   - Click "Connect"
   - Select "Connect your application"
   - Copy connection string
   - Format: `mongodb+srv://username:password@cluster.mongodb.net/database`

4. **Update .env:**
   ```env
   MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/digital-healthcare
   ```

---

## Common Issues & Solutions

### Issue: "MongoDB connection error"
**Solution:**
```bash
# Check if MongoDB is running
mongod

# If error persists, check connection string in .env
# Local: mongodb://localhost:27017/digital-healthcare
# Cloud: mongodb+srv://user:pass@cluster.mongodb.net/db
```

### Issue: "Port 5000 already in use"
**Solution:**
```bash
# Windows - Find and kill process
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# Or change port in .env
PORT=5001
```

### Issue: "Port 3000 already in use"
**Solution:**
```bash
# Frontend will ask to use different port
# Answer: Y
```

### Issue: "Cannot find module 'express'"
**Solution:**
```bash
cd backend
npm install

cd ../frontend
npm install
```

### Issue: "Backend not responding"
**Checklist:**
- ✅ Backend running? (`npm run dev`)
- ✅ Port 5000 correct?
- ✅ MongoDB connected?
- ✅ .env file configured?

### Issue: "QR code not generating"
**Solution:**
- Verify patient data is complete
- Check browser console for errors
- Refresh page

---

## Testing the Application

### Test Patient Flow

1. **Register:**
   - Email: `patient1@test.com`
   - Password: `password123`
   - Name: `John Doe`
   - Get Health ID: `health****`

2. **Add Medication:**
   - Navigate to Medications
   - Add: Aspirin, 500mg, Mon-Fri 8:00 AM
   - Submit

3. **Add Vaccination:**
   - Navigate to Vaccinations
   - Add: COVID-19, 2024-01-25, 10:00 AM
   - Submit

4. **Generate QR:**
   - Go to QR Code section
   - Your QR code displays with all info

5. **Try AI Chat:**
   - Ask: "What should I do about fever?"
   - Get health advice response

### Test Doctor Flow

1. **Login:**
   - Email: doctor@gmail.com
   - Password: health123

2. **Search Patient:**
   - Enter Health ID from step 1
   - View patient details

3. **Update Records:**
   - Add medication for patient
   - Add vaccination for patient
   - Scan the QR code

---

## Production Deployment

### Frontend Deployment (Vercel)

```bash
# Build for production
cd frontend
npm run build

# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

### Backend Deployment (Heroku)

```bash
# Install Heroku CLI
# Download from heroku.com

# Login
heroku login

# Create app
heroku create your-app-name

# Set environment variables
heroku config:set MONGODB_URI=your_mongodb_uri
heroku config:set JWT_SECRET=your_secret

# Deploy
git push heroku main
```

---

## Performance Tips

1. **Database Indexing:**
   ```javascript
   // Already included in models
   healthId: { type: String, unique: true, index: true }
   email: { type: String, unique: true, index: true }
   ```

2. **Caching:**
   - Patient data cached in localStorage
   - API responses minimal

3. **Pagination:**
   - Implement for large patient lists (future)

4. **CDN:**
   - Deploy frontend to CDN (Vercel, Netlify)

---

## Security Checklist

✅ Passwords hashed with bcryptjs
✅ JWT authentication on all protected routes
✅ CORS enabled for development
✅ Environment variables for secrets
✅ No sensitive data in frontend code
✅ QR codes encoded with patient data
✅ HTTPS recommended for production

---

## Next Steps

1. **Customize Branding:**
   - Update colors in CSS files
   - Change app name in frontend

2. **Add More Features:**
   - Email notifications
   - SMS alerts
   - Appointment scheduling
   - Telemedicine

3. **Deploy:**
   - Setup MongoDB Atlas
   - Deploy backend (Heroku/AWS)
   - Deploy frontend (Vercel/Netlify)

4. **Monitor:**
   - Setup error tracking (Sentry)
   - Monitor performance (DataDog)
   - Check logs regularly

---

## Support & Documentation

- **Backend API Docs**: See `backend/README.md`
- **Frontend Guide**: See `frontend/README.md`
- **Main Documentation**: See `README.md`
- **Email Support**: support@digitalhealthcare.com

---

## Version Info

- **Project**: Digital Healthcare System v1.0.0
- **Node.js**: 14+ recommended
- **React**: 18.2.0
- **Express**: 4.18.2
- **MongoDB**: 4.0+

---

**Happy coding! 🚀**

Need help? Check the README files in each directory or contact support.
