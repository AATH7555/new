# MongoDB Atlas Quick Start

## What You Need to Do:

1. **Sign up** at https://www.mongodb.com/cloud/atlas
2. **Create FREE cluster** (M0 tier)
3. **Create database user** with strong password
4. **Whitelist IP** (Allow all 0.0.0.0/0 for now)
5. **Get connection string** from Atlas dashboard
6. **Update `.env`** with connection string:
   ```
   MONGODB_URI=mongodb+srv://user:pass@cluster.mongodb.net/digital-healthcare?retryWrites=true&w=majority
   ```
7. **Restart backend** and test

## Connection String Format:
```
mongodb+srv://USERNAME:PASSWORD@CLUSTER_NAME.mongodb.net/DATABASE_NAME?retryWrites=true&w=majority
```

## Your Current Status:
- ✅ Backend configured to use MongoDB URI from .env
- ✅ Ready to connect to cloud database
- ⏳ Waiting: You to set up Atlas account and get connection string

## Next: 
- Open [MONGODB_ATLAS_SETUP.md](MONGODB_ATLAS_SETUP.md) for detailed step-by-step instructions
- Or tell me your connection string and I'll configure it for you

