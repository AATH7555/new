# 🏥 How to Run the Digital Healthcare System

## 🚀 Starting the Application

### Step 1: Start the Application
```bash
cd d:\new\pro
start.bat
```

Or just double-click the **start.bat** file.

**Wait 5-10 seconds** for both backend and frontend to start.

---

## 📱 Patient Portal

### Access Patient Portal
1. Open browser: **http://localhost:3000**
2. You'll see the Login page

### Option A: Create New Patient Account
1. Click on **"Patient"** tab
2. Click **"Create Account"** link
3. Fill in:
   - **Name**: Your full name
   - **Email**: Your email address
   - **Password**: 6+ characters
   - **Confirm Password**: Same password
4. Click **"Create Account"**
5. ✅ You're logged in! See your Dashboard

### Option B: Login as Existing Patient
1. Click on **"Patient"** tab
2. Enter **Email**: `john@example.com`
3. Enter **Password**: `password123`
4. Click **"Login"**
5. ✅ Patient Dashboard appears

### Patient Dashboard Features
- 📊 **View Health Stats** - Age, Blood Type, etc.
- 💊 **Medications** - See all medications you're taking
- 💉 **Vaccinations** - View vaccination history
- 📱 **Generate QR Code** - Create your health QR code
- 🤖 **Health AI Chat** - Talk to health assistant
- ❓ **Help & Support** - Get information

---

## 👨‍⚕️ Doctor Portal

### Access Doctor Portal
1. Open browser: **http://localhost:3000**
2. You'll see the Login page

### Login as Doctor
1. Click on **"Doctor"** tab
2. Click **"Doctor Login"** button
3. Credentials are **pre-filled** automatically:
   - **Email**: doctor@gmail.com
   - **Password**: health123
4. Click **"Login"**
5. ✅ Doctor Dashboard appears

### Doctor Dashboard - Search Patient
1. On left side: **"Find Patient"** section
2. Enter **Health ID** (example: `health0001`)
3. Click **"Search"** button
4. Click on patient from results

### Doctor Functions (Click any button to go to full page)

#### 📅 **Appointments**
- View booked appointments

#### 💊 **Medications**
- See all patient's current medications
- View dosage, frequency, reason

#### 💊 **Manage Medications**
- Add new medication for patient
- Update existing medications
- Delete medications

#### 💉 **Vaccinations**
- View patient's vaccination records
- See vaccination status

#### 🩹 **Manage Vaccinations**
- Add new vaccination record
- Update vaccination details
- Track next due dates

#### 💉 **Vaccination View**
- Detailed vaccination history with all info

#### 👤 **Profile**
- View complete patient profile
- See all personal details

#### 🔍 **QR Scanner**
- Scan patient's QR code
- View complete patient health data:
  - 👤 Profile details
  - 💊 All medications
  - 💉 All vaccinations
- Shows dosage, frequency, vaccination dates, batch numbers

---

## 🔑 Quick Test Credentials

### Patient Account (Already Created)
```
Email: john@example.com
Password: password123
```

### Doctor Account
```
Email: doctor@gmail.com
Password: health123
```

---

## 📍 URLs

| Component | URL |
|-----------|-----|
| 🌐 Frontend | http://localhost:3000 |
| ⚙️ Backend API | http://localhost:5000 |

---

## ⚡ Quick Steps

### For Patient:
1. Go to **http://localhost:3000**
2. Click **"Patient"** tab
3. Click **"Create Account"** or login with `john@example.com / password123`
4. ✅ See your health dashboard

### For Doctor:
1. Go to **http://localhost:3000**
2. Click **"Doctor"** tab
3. Click **"Doctor Login"** (credentials auto-filled)
4. Enter Health ID (example: `health0001`)
5. Click **"Search"**
6. Click patient to select
7. Click any button to view patient details
8. Click **"Back"** button to return to dashboard

---

## 🐛 Troubleshooting

### Application won't start?
```bash
cd d:\new\pro
npm start
```

### Port already in use?
- Close any other applications using ports 3000 or 5000
- Or restart the application

### Database connection error?
- Make sure MongoDB connection is working
- Check `backend/.env` file for database URL

---

## ✨ Features

✅ Patient Registration & Login
✅ Doctor Login & Search
✅ Medication Management
✅ Vaccination Tracking
✅ QR Code Generation & Scanning
✅ Health AI Chatbot
✅ Full Patient Health Records
✅ Real-time Data Updates

**Enjoy using the Digital Healthcare System! 🏥**
