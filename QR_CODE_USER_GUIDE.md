# QR Code Feature - User Guide

## 🎯 Overview

The QR Code feature allows doctors to generate scannable QR codes containing all of a patient's vaccination and medication information. This QR code can be downloaded, printed, or scanned by any QR code reader to view the patient's complete health data.

---

## 📖 Step-by-Step Usage Guide

### Step 1: Access Patient Records
```
1. Login to Doctor Portal
2. Click on a patient from the "All Patients" list
   OR
   Search for patient by entering their Health ID
3. Click on the patient name/card to view details
```

### Step 2: Navigate to QR Code Generator
```
1. Once patient is selected, you'll see action tabs:
   - 📅 Appointments
   - 💊 Medications
   - 🩹 Manage Meds
   - 🩸 Vaccinations
   - 💉 Vaccination View
   - 👤 Profile
   - 🔍 Scanner
   - 📱 Generate QR  ← Click this
```

### Step 3: Generate QR Code
```
1. Click the "Generate QR" tab button
2. Click "Show QR Code" button
3. The QR code will display with:
   - Patient name, health ID, and email
   - Vaccination count
   - Medication count
```

### Step 4: Use QR Code
```
Option A - Download QR Code:
  1. Click "Download" button
  2. QR code saves as PNG image
  3. Filename format: PatientName_QRCode_[timestamp].png
  4. Share via email or messaging

Option B - Print QR Code:
  1. Click "Print" button
  2. Print preview opens
  3. Customize print settings
  4. Print and distribute

Option C - Share Directly:
  1. Take screenshot of QR code
  2. Share screenshot via email/messaging
  3. Recipient scans with any QR reader
```

### Step 5: Scan QR Code (Recipient)
```
1. Use any QR code scanner app
2. Point camera at QR code
3. App decodes the JSON data
4. Shows complete patient information:
   - Name, Health ID, Email
   - Phone, Date of Birth, Blood Type
   - All vaccinations with dates
   - All medications with dosage info
```

---

## 📊 QR Code Data Structure

When scanned, the QR code decodes to show:

```
PATIENT INFORMATION
├─ Name: [Patient Full Name]
├─ Health ID: [Unique Health ID]
├─ Email: [Patient Email]
├─ Phone: [Patient Phone]
├─ Date of Birth: [DOB]
└─ Blood Type: [Blood Type]

VACCINATIONS
├─ Completed Vaccinations:
│  ├─ Vaccine Name, Date, Status
│  ├─ Vaccine Name, Date, Status
│  └─ ...
└─ Scheduled Vaccinations:
   ├─ Vaccine Name, Scheduled Date, Days Until
   ├─ Vaccine Name, Scheduled Date, Days Until
   └─ ...

MEDICATIONS
├─ Medication 1: [Name], [Dosage], [Schedule]
├─ Medication 2: [Name], [Dosage], [Schedule]
└─ ...
```

---

## 🔒 Security Considerations

⚠️ **Important Notes:**

1. **Patient Privacy**: QR codes contain patient health information
   - Keep QR codes secure and confidential
   - Only share with authorized healthcare providers
   - Only share with the patient themselves

2. **Access Control**: Only doctors can generate QR codes
   - Patient data is protected by authentication
   - QR generation logs can be audited

3. **Data Format**: QR codes store JSON-encoded data
   - No encryption currently implemented
   - Consider secure channels for transmission
   - Can be enhanced with encryption if needed

4. **Sharing Best Practices**:
   - Use secure email for transmission
   - Use encrypted messaging apps
   - Use password-protected PDFs if printing
   - Limit distribution to necessary parties only

---

## 💡 Use Cases

### 1. **Patient Referral**
```
Doctor A → Doctor B
- Generate QR code of patient's health records
- Patient scans QR code at specialist's office
- Specialist immediately sees vaccination & medication history
```

### 2. **Hospital Records**
```
Doctor → Hospital/Clinic
- Print QR code and attach to patient file
- Nurses/staff scan to verify medications quickly
- Emergency access to vaccination information
```

### 3. **Travel Documentation**
```
Doctor → Traveler
- Generate QR code for vaccination records
- Patient carries on phone or prints copy
- Show at airports/borders as proof of vaccination
```

### 4. **Home Health Care**
```
Doctor → Home Care Provider
- Share QR code of patient's current medications
- Provider scans during home visit
- Ensures they have up-to-date medication list
```

### 5. **Patient Backup**
```
Doctor → Patient
- Generate QR code with complete health history
- Patient keeps on phone or printed
- Backup in case of lost records
```

---

## 🔄 Workflow Diagram

```
┌─────────────────┐
│  Doctor Login   │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Select Patient  │
└────────┬────────┘
         │
         ▼
┌──────────────────────┐
│ Click "Generate QR"  │
└────────┬─────────────┘
         │
         ▼
┌──────────────────────┐
│ Click "Show QR Code" │
└────────┬─────────────┘
         │
    ┌────┴──────┐
    │            │
    ▼            ▼
┌────────────┐  ┌────────────┐
│  Download  │  │   Print    │
│    PNG     │  │  Physical  │
└────┬───────┘  └─────┬──────┘
     │                │
     ▼                ▼
   Share           Distribute
     │                │
     └────────┬───────┘
              │
              ▼
         ┌─────────────────┐
         │ Scan QR Code    │
         │ View All Data   │
         └─────────────────┘
```

---

## 🛠️ Technical Details

### QR Code Specifications
- **Format**: PNG image file (downloadable)
- **Size**: 300x300 pixels
- **Error Correction**: Level H (30% data recovery)
- **Data Type**: JSON
- **Compression**: Built-in QR compression

### Browser Compatibility
- ✅ Chrome (Latest)
- ✅ Firefox (Latest)
- ✅ Safari (Latest)
- ✅ Edge (Latest)
- ✅ Mobile Browsers (iOS Safari, Chrome Mobile)

### Data Encoding Example
```json
{
  "patientId": "60d5ec49c1234567890abc12",
  "name": "John Doe",
  "healthId": "health0001",
  "email": "john@example.com",
  "phone": "555-1234",
  "dateOfBirth": "1990-01-15",
  "bloodType": "O+",
  "vaccinations": [
    {
      "name": "COVID-19",
      "date": "2024-01-20",
      "type": "completed"
    },
    {
      "name": "Influenza",
      "date": "2024-06-15",
      "type": "scheduled"
    }
  ],
  "medications": [
    {
      "name": "Aspirin",
      "dosage": "100mg",
      "schedule": "Once daily"
    }
  ]
}
```

---

## ❓ FAQ

**Q: How long does the QR code remain valid?**
A: QR codes don't expire. They'll work indefinitely as they're static data. However, the medical information they contain should be updated when patient records are updated.

**Q: Can I regenerate the QR code?**
A: Yes! Every time you click "Show QR Code", it regenerates from the current patient data in the system.

**Q: Is the QR code encrypted?**
A: Currently, the QR code contains plain JSON data. No encryption is applied. Treat the QR code as confidential patient information.

**Q: What QR code scanner should I use?**
A: Any QR code reader app works:
- Google Lens (Android/iOS)
- iPhone built-in camera
- Android built-in scanner
- Dedicated QR apps from app stores

**Q: Can I customize the QR code?**
A: Currently, no. But the feature can be enhanced with:
- Custom logo/watermark
- Different size options
- Color customization

**Q: What if patient data changes?**
A: Simply regenerate the QR code. The new code will reflect the current data from the database.

---

## 📱 Mobile Scanning Tips

### iPhone
1. Open Camera app
2. Point at QR code
3. Tap notification that appears
4. View decoded data

### Android
1. Open Google Lens (via Google app)
2. Point camera at QR code
3. Tap URL or data shown
4. View decoded data

### Third-Party Apps
- QR Code Reader (free)
- Barcode Scanner
- Kaspersky QR Scanner
- TikTok (can scan QR codes)

---

## 🆘 Troubleshooting

| Problem | Solution |
|---------|----------|
| QR code won't generate | Ensure patient is selected and has data |
| Download button doesn't work | Check browser permissions, try different browser |
| Print dialog doesn't open | Ensure pop-ups are allowed in browser settings |
| QR code won't scan | Ensure QR code image is clear, good lighting |
| Data shows incomplete | Verify patient records are up-to-date in system |

---

## 📞 Support

For technical issues:
1. Check browser console for errors (F12)
2. Try refreshing the page
3. Clear browser cache and cookies
4. Try different browser
5. Contact system administrator

---

**Last Updated**: Current Session  
**Status**: Feature Ready for Production  
**Version**: 1.0
