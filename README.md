# Nexon Folio Website

A modern personal portfolio web application built with React, GSAP animations, EmailJS contact, Leaflet maps, and Firebase auth/storage/Firestore. The repository also contains a Sanity Studio to manage blog content.

## Tech Stack
- React 17 (Create React App)
- SCSS (Sass)
- GSAP (local bonus package) for animations
- EmailJS for contact form
- React Router v6
- Leaflet + React Leaflet for maps
- Firebase (Auth, Firestore, Storage)
- Sanity Studio v2 for blogging (`portfolio-blog/`)

## Repository Layout
```
/ (root)
├─ src/                    React web app source
├─ public/                 Static assets
├─ portfolio-blog/         Sanity Studio (content studio for blog)
├─ gsap-bonus.tgz          Local GSAP bonus package
├─ package.json            Web app package
└─ portfolio-blog/package.json  Sanity Studio package
```

## Prerequisites
- Node.js 16+ and npm (or yarn)
- A Firebase project (if you plan to use your own credentials)
- A Sanity account and project (optional, only if you will run the Studio)

## Quick Start
Install dependencies at the root for the web app:
```bash
npm install
npm start
```
This runs the React app at `http://localhost:3000/`.

Install and run Sanity Studio:
```bash
cd portfolio-blog
npm install
npx sanity login --with-ci-token=no
npm run start
```
The Studio runs at `http://localhost:3333/`.

## Available Scripts (root)
- `npm start`: Start React dev server
- `npm run build`: Production build
- `npm test`: Run tests
- `npm run eject`: Eject CRA (irreversible)

Dev utilities (present):
- `npm run dev`: Uses nodemon (not required for CRA; ignore unless you add a custom server)

## Available Scripts (portfolio-blog)
- `npm run start`: Start Sanity Studio locally
- `npm run build`: Build the Studio for production

## Configuration
### Firebase
Current config lives in `src/firebase.js`. For production, move secrets to environment variables.
Recommended `.env` at project root:
```bash
REACT_APP_FIREBASE_API_KEY=...
REACT_APP_FIREBASE_AUTH_DOMAIN=...
REACT_APP_FIREBASE_PROJECT_ID=...
REACT_APP_FIREBASE_STORAGE_BUCKET=...
REACT_APP_FIREBASE_MESSAGING_SENDER_ID=...
REACT_APP_FIREBASE_APP_ID=...
REACT_APP_FIREBASE_MEASUREMENT_ID=...
```
Then update `src/firebase.js` to read from `process.env.REACT_APP_*` variables.

### EmailJS
If the contact form uses EmailJS, configure your service, template, and public key and expose them via `.env` as well (example names):
```bash
REACT_APP_EMAILJS_PUBLIC_KEY=...
REACT_APP_EMAILJS_SERVICE_ID=...
REACT_APP_EMAILJS_TEMPLATE_ID=...
```

### Maps (Leaflet)
Leaflet works out of the box with public tile servers. If you use a paid tile provider, keep the key in `.env`.

### GSAP Bonus
The project references a local package `gsap-bonus.tgz`. Ensure you have a valid GSAP Club Greensock license. If you do not, replace the dependency with the standard `gsap` from npm.

## Building
Create a production build of the React app:
```bash
npm run build
```
Outputs to `build/`. Serve it with any static host (Vercel, Netlify, Nginx, etc.).

Build Sanity Studio:
```bash
cd portfolio-blog
npm run build
```
This outputs a static build in `./dist/` (inside `portfolio-blog/`). You can deploy it separately or host behind your site.

## Deployment
- React app: Deploy the `build/` directory to your host.
- Sanity Studio: Deploy `portfolio-blog/dist/` as a separate site or on a protected path/subdomain.

## Project Highlights
- Animated intro and sections with GSAP
- Typed animated letters component
- Portfolio sections with images under `public/portfolio/`
- Blog managed with Sanity (schemas in `portfolio-blog/schemas/`)
- Contact page powered by EmailJS and a Leaflet map
- Optional Google auth via Firebase

## Troubleshooting
- If `gsap-bonus.tgz` fails to install, confirm you have access; otherwise switch to `gsap` from npm.
- If CRA fails due to Node version, use Node 16/18.
- If maps do not render, ensure CSS for Leaflet is included and tiles are reachable.
- If EmailJS fails, verify keys, service/template IDs, and network requests in devtools.

## License
This project is UNLICENSED. Review third‑party licenses (GSAP, Sanity, Firebase, Leaflet, EmailJS) before distribution.
