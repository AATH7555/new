# 🗄️ Database Configuration

## MongoDB Setup

The Digital Healthcare System uses **MongoDB** as the primary database to store all patient and medical data.

### Database Location
- **Local Development**: `mongodb://localhost:27017/digital-healthcare`
- **Database Name**: `digital-healthcare`

### Database Collections

#### 1. **Patients Collection**
Stores patient personal and medical information.
```
- _id (ObjectId)
- healthId (String) - Auto-generated
- name (String)
- email (String)
- password (String - encrypted)
- phone (String)
- dateOfBirth (Date)
- gender (String)
- bloodType (String)
- allergies (Array)
- medicalHistory (Array)
- createdAt (Date)
- updatedAt (Date)
```

#### 2. **Doctors Collection**
Stores doctor professional information.
```
- _id (ObjectId)
- name (String)
- email (String)
- password (String - encrypted)
- medicalLicense (String)
- specialization (String)
- hospitalAffiliation (String)
- yearsOfExperience (Number)
- phone (String)
- createdAt (Date)
```

#### 3. **Tablets Collection**
Stores medication/tablet prescriptions.
```
- _id (ObjectId)
- patientId (ObjectId - Reference)
- tabletName (String)
- dosage (String)
- schedule (Array of Objects)
  - day (String)
  - time (String)
- startDate (Date)
- endDate (Date)
- weeklyReport (Array)
- createdAt (Date)
- updatedAt (Date)
```

#### 4. **Vaccinations Collection**
Stores vaccination records.
```
- _id (ObjectId)
- patientId (ObjectId - Reference)
- vaccinationName (String)
- status (String) - completed, pending, scheduled
- vaccinationDetails (Array of Objects)
  - date (Date)
  - time (String)
  - location (String)
- futureVaccinations (Array of Objects)
  - name (String)
  - scheduledDate (Date)
- weeklyReport (Array)
- createdAt (Date)
- updatedAt (Date)
```

#### 5. **Appointments Collection**
Stores appointment bookings.
```
- _id (ObjectId)
- patientId (ObjectId - Reference)
- doctorId (ObjectId - Reference)
- appointmentDate (Date)
- appointmentTime (String)
- reason (String)
- status (String) - scheduled, completed, cancelled
- notes (String)
- createdAt (Date)
- updatedAt (Date)
```

#### 6. **HealthAlerts Collection**
Stores health notifications and reminders.
```
- _id (ObjectId)
- patientId (ObjectId - Reference)
- alertType (String) - medication-reminder, vaccination-due, appointment-reminder, health-warning
- title (String)
- message (String)
- dueDate (Date)
- isRead (Boolean)
- createdAt (Date)
```

#### 7. **UserProfiles Collection**
Stores extended profile information.
```
- _id (ObjectId)
- userId (ObjectId)
- userType (String) - patient, doctor
- phone (String)
- dateOfBirth (Date)
- gender (String)
- bloodType (String)
- address (String)
- city (String)
- state (String)
- zipCode (String)
- allergies (Array)
- specialization (String) - For doctors
- medicalLicense (String) - For doctors
- hospitalAffiliation (String) - For doctors
- yearsOfExperience (Number) - For doctors
- emergencyContact (Object)
  - name (String)
  - phone (String)
  - relation (String)
- profilePicture (String)
- createdAt (Date)
- updatedAt (Date)
```

#### 8. **MedicalReports Collection**
Stores medical reports and documents.
```
- _id (ObjectId)
- patientId (ObjectId - Reference)
- doctorId (ObjectId - Reference)
- reportType (String) - general-health, lab-report, prescription, discharge-summary
- title (String)
- description (String)
- findings (String)
- recommendations (String)
- attachmentUrl (String)
- createdAt (Date)
```

## Initialization

### Run Database Initialization
```bash
cd backend
node scripts/initializeDatabase.js
```

This will:
- Connect to MongoDB
- Clear existing data
- Create 3 sample patients
- Create 3 sample doctors
- Create 3 medications
- Create 3 vaccinations
- Create 3 appointments
- Create 3 health alerts
- Create user profiles

### Sample Login Credentials
**Patient:**
- Email: `john@example.com`
- Password: `password123`

**Doctor:**
- Email: `doctor.james@example.com`
- Password: `password123`

## Data Storage

All data is automatically saved to MongoDB including:
- ✅ Patient health records
- ✅ Doctor information
- ✅ Medications and dosages
- ✅ Vaccination records
- ✅ Appointment bookings
- ✅ Health alerts and notifications
- ✅ User profiles
- ✅ Medical reports
- ✅ Health IDs (Auto-generated)

## Backup & Export

To export data:
```bash
# Export patients collection
mongoexport --db digital-healthcare --collection patients --out patients.json

# Export all collections
mongoexport --db digital-healthcare --collection doctors --out doctors.json
mongoexport --db digital-healthcare --collection tablets --out tablets.json
mongoexport --db digital-healthcare --collection vaccinations --out vaccinations.json
```

## Database Indexes

For optimal performance, indexes are automatically created on:
- Patient healthId (Unique)
- Patient email (Unique)
- Doctor email (Unique)
- Doctor medicalLicense (Unique)
- Tablet patientId
- Vaccination patientId
- Appointment patientId & doctorId
- HealthAlert patientId

---

**Last Updated**: January 24, 2026
**Database Status**: ✅ Running & Configured
