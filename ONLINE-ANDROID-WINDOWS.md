# Online Android + Windows UMS deployment

## Architecture
- React/Vite frontend: host on HTTPS (Vercel, Netlify, or your university web server)
- Node/Express API: host on a Node-capable server (Render, Railway, VPS, or university server)
- MySQL: managed MySQL or secure university database server
- Set frontend `VITE_API_URL` to the public API URL (e.g. `https://api.yourdomain.edu.et/api`)
- Set backend `FRONTEND_URL` to your public frontend origin; configure production DB and strong JWT secret.

## Install on Android and Windows (PWA)
1. Deploy frontend over HTTPS and backend/API with internet access.
2. Android: open the frontend URL in Chrome > menu > Install app / Add to Home screen.
3. Windows: open the URL in Edge or Chrome > Install app.
4. Users sign in with their assigned UMS accounts.
Note: the service worker caches app shell only; it does NOT cache private student data or API responses.

## Native Android APK build (Capacitor wrapper)
1. Install Android Studio and Android SDK.
2. In frontend folder:
   ```bash
   npm install
   npm run build
   npx cap add android
   npx cap sync android
   npx cap open android
   ```
3. In Android Studio choose Build > Build APK(s), or generate a signed app bundle for release.
4. Set `VITE_API_URL` to the public HTTPS API before building. Do not use localhost for production.
5. For release, configure app signing and test on real devices.

## Important production checklist
- Use HTTPS everywhere and strong secrets.
- Do not expose MySQL publicly; only API server should access it.
- Remove/disable the `/api/auth/create-admin` setup route after initial admin creation.
- Add backups, audit logs, rate limiting, validation, and monitoring.
- Configure CORS for only your actual production frontend domain.
- The sample app is a starter and needs complete modules, tested workflows, and security review before real university use.
