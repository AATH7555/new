# MongoDB Atlas Setup Guide

## Step 1: Create MongoDB Atlas Account
1. Go to https://www.mongodb.com/cloud/atlas
2. Click "Sign Up"
3. Create account with email and password
4. Verify email address

## Step 2: Create a Project
1. Click "Create a Project"
2. Name it "Digital Healthcare" (or your choice)
3. Click "Next"
4. Click "Create Project"

## Step 3: Create a Database Cluster
1. Click "Build a Database"
2. Choose **FREE** tier (M0 - suitable for development/testing)
3. Select your region (choose closest to you):
   - Asia Pacific (if in India/Asia)
   - Europe (if in Europe)
   - North America (if in USA/Canada)
4. Give cluster a name: `digital-healthcare-cluster`
5. Click "Create Deployment"

## Step 4: Create Database User
1. In "Security" section, click "Database Access"
2. Click "Add New Database User"
3. Enter:
   - **Username**: `healthcare_user`
   - **Password**: Create a strong password (save this!)
4. Keep "Built-in Role" as **readWriteAnyDatabase**
5. Click "Add User"

## Step 5: Add IP Whitelist
1. In "Security" section, click "Network Access"
2. Click "Add IP Address"
3. For development: Click "Allow Access from Anywhere" (0.0.0.0/0)
   - ⚠️ For production: Add specific IPs only
4. Click "Confirm"

## Step 6: Get Connection String
1. Click "Databases" in left sidebar
2. Click "Connect" button on your cluster
3. Select "Drivers" (if not already selected)
4. Choose Node.js driver
5. Copy the connection string that looks like:
   ```
   mongodb+srv://healthcare_user:YOUR_PASSWORD@digital-healthcare-cluster.mongodb.net/digital-healthcare?retryWrites=true&w=majority
   ```

## Step 7: Update Backend .env File
Replace the `MONGODB_URI` in `backend/.env`:

```env
MONGODB_URI=mongodb+srv://healthcare_user:YOUR_PASSWORD@digital-healthcare-cluster.mongodb.net/digital-healthcare?retryWrites=true&w=majority
```

### Replace:
- `healthcare_user` - Your database username
- `YOUR_PASSWORD` - Your database password (from Step 4)
- `digital-healthcare-cluster` - Your cluster name (from Step 3)

## Step 8: Test Connection
1. Restart your backend server:
   ```bash
   cd backend
   node server.js
   ```

2. You should see:
   ```
   ✅ MongoDB connected successfully
   ```

## Step 9: Verify Data
1. Go back to MongoDB Atlas dashboard
2. Click "Collections" on your cluster
3. You should see your database data there

---

## Production Settings

For production deployment:

```env
# Production settings
MONGODB_URI=mongodb+srv://healthcare_user:YOUR_PASSWORD@digital-healthcare-cluster.mongodb.net/digital-healthcare?retryWrites=true&w=majority
NODE_ENV=production
JWT_SECRET=use_a_very_strong_random_key_in_production
```

### Before going live:
1. ✅ Use strong, unique password
2. ✅ Set specific IP whitelist (not 0.0.0.0/0)
3. ✅ Enable IP whitelist
4. ✅ Use environment variables for secrets
5. ✅ Enable database encryption
6. ✅ Set up automated backups

---

## Troubleshooting

**Connection Timeout Error:**
- Check IP whitelist includes your IP
- Verify username and password are correct
- Ensure network is stable

**Authentication Failed:**
- Double-check password has no special characters requiring escaping
- If password has special chars, encode it with URL encoding
- Example: `@` becomes `%40`, `:` becomes `%3A`

**Database Not Found:**
- MongoDB Atlas creates database automatically on first write
- Run application once to initialize database
- Check database name matches in connection string

---

## Backup & Monitoring

- **Automatic Backups**: MongoDB Atlas automatically backs up data
- **View Backups**: Go to "Backup" in left sidebar
- **Monitoring**: Dashboard shows real-time metrics
- **Alerts**: Set up alerts for high CPU/Memory usage

