Hosting with Docker (recommended)

Quick steps (VPS or local machine with Docker):

1. Copy env file and set values:

   cp .env.example .env
   # edit .env and set MONGO_URI if not using local mongo

2. Build and start:

   docker compose up -d --build

3. Visit the app:

   - Frontend: http://<HOST_IP>:3000
   - Backend: http://<HOST_IP>:5000

Notes and tips:
- In production you may want to use a managed MongoDB (MongoDB Atlas). Set `MONGO_URI` in `.env` to the Atlas connection string.
- If deploying on a cloud VM, open ports 3000, 5000, and 27017 (or restrict Mongo to localhost and use Atlas instead).
- For an internet-exposed public URL without changing firewall, you can run `start_ngrok.bat` and use the generated ngrok URL.

Alternative: Platform deployments
- Frontend: Vercel (recommended for static React apps)
- Backend: Render or Railway (they support Node web services and env vars)

If you want, I can:
- Prepare Render/Vercel specific config files
- Build Docker images and push to Docker Hub for one-click deploy
