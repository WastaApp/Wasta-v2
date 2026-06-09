# WASTA Website & App Deployment Guide

## Current Status

This project is a Vite + React + TypeScript frontend. It is deployable as a website today.

Important: the current project uses mock data. It is not yet a real backend-connected marketplace. Customers, providers, bookings, payments, WhatsApp, OTP, invoices and admin actions are UI/demo flows until a backend/database is connected.

## Local Test

```bash
npm ci
npm run dev
```

Open the local URL shown by Vite.

## Production Build Test

```bash
npm run build
npm run preview
```

If build succeeds, it is ready for Vercel deployment.

## GitHub Upload

1. Create a new GitHub repository, for example: `wasta-marketplace`.
2. Extract this ZIP.
3. Open the project folder in VS Code.
4. Run:

```bash
git init
git add .
git commit -m "Initial WASTA marketplace frontend"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/wasta-marketplace.git
git push -u origin main
```

## Deploy on Vercel

1. Go to Vercel.
2. Add New Project.
3. Import the GitHub repository.
4. Framework preset: Vite.
5. Build command: `npm run build`.
6. Output directory: `dist`.
7. Install command: `npm ci`.
8. Deploy.

The included `vercel.json` handles refresh/reload on nested routes like `/portal/admin`.

## Environment Variables

No environment variables are required for the current mock frontend.

When backend is added, create these in Vercel Project Settings:

```env
VITE_API_BASE_URL=https://api.yourdomain.com
VITE_GOOGLE_MAPS_KEY=your_google_maps_key
VITE_STRIPE_PUBLIC_KEY=your_stripe_public_key
```

Never add secret backend keys to a Vite frontend.

## Custom Domain

1. Buy a domain, for example: `wasta.ae` or `.com`.
2. In Vercel, open Project > Settings > Domains.
3. Add your domain.
4. Update DNS records as Vercel instructs.

## Mobile App Options

### Option 1: PWA
This package includes a basic web app manifest. Users can install it from browser to home screen. This is fastest but not a full App Store/Play Store app.

### Option 2: Capacitor Wrapper
Use this if you want Android/iPhone apps from the same website.

```bash
npm install @capacitor/core @capacitor/cli
npx cap init WASTA com.wasta.app
npm run build
npx cap add android
npx cap add ios
npx cap sync
```

You will need Android Studio for Android and macOS/Xcode for iOS.

### Option 3: Real Native App
Build a React Native/Expo app. This is the best long-term option for push notifications, GPS, provider tracking, camera uploads, and smoother mobile UX.

## Backend Roadmap

To make WASTA a real marketplace, build these next:

1. PostgreSQL database
2. User authentication / OTP
3. Customer onboarding
4. Provider onboarding and document approval
5. Booking API
6. Provider assignment API
7. Payment integration
8. WhatsApp notifications
9. Invoice generation
10. Admin audit logs
11. File uploads
12. Mobile push notifications

## Recommended Backend Stack

- Supabase or Neon PostgreSQL
- Next.js API routes or NestJS backend
- Prisma ORM
- Stripe Connect
- WhatsApp Cloud API
- Firebase Cloud Messaging
- Google Maps API

## Go-Live Checklist

- Build passes without error
- Vercel deployment works
- All routes refresh correctly
- Domain connected
- SSL active
- Mobile layout checked
- Privacy Policy added
- Terms & Conditions added
- Contact details added
- Backend integration plan approved
