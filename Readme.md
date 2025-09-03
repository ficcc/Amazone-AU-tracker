Price Tracker React App
This is a web application built with React and Firebase that allows users to track product prices from Amazon AU and JB Hi-Fi. Users can add products by URL, and the app will scrape the name, price, and image, storing the data in a real-time Firestore database.

Live Demo: https://web-tracker-312f2.web.app/
Features
Add Products via URL: Simply paste a product link from Amazon AU.

Live Web Scraping: A Firebase Cloud Function backend scrapes product data in real-time.

Real-time Database: Cloud Firestore syncs product data instantly across sessions.

Price Change Indicators: Visual cues show if a price has increased (red down arrow) or decreased (green up arrow) since the last refresh.

Search and Filter: Easily find tracked products with a live search bar.

One-Click Refresh: Update all product prices simultaneously.

Easy Management: Delete tracked products or visit the original product page with a single click.

Technology Used
Frontend
React: A JavaScript library for building dynamic user interfaces.

Tailwind CSS: A utility-first CSS framework for rapid and responsive styling.

Firebase SDK (v9): For seamless frontend-backend communication (Authentication, Firestore, Functions).

Lucide React: For clean, lightweight SVG icons.

Backend & Database
Firebase: A comprehensive platform for backend services.

Firebase Authentication: Used for creating anonymous, unique user sessions to store data securely.

Cloud Firestore: A NoSQL, real-time database used to store all tracked product information for each user.

Cloud Functions for Firebase: A serverless backend running Node.js to handle the web scraping logic, ensuring it's scalable and secure.

Web Scraping
Axios: A promise-based HTTP client for making requests to product pages.

Cheerio: A fast and flexible implementation of core jQuery designed for the server to parse and manipulate HTML.

ScraperAPI: A proxy service used to prevent scraping requests from being blocked by e-commerce sites.

Hosting
Firebase Hosting: To deploy and serve the React frontend via a global CDN.

Project Workflow & Setup Instructions
This project is structured as a monorepo with a client folder for the React app and a functions folder for the Firebase backend.

1. Firebase Project Setup
   Go to the Firebase Console and create a new project.

Upgrade your project to the "Blaze (Pay as you go)" plan. This is required for Cloud Functions to make external network requests to other websites. A generous free tier is included.

In the Firebase dashboard, Enable the following services:

Authentication: Go to the "Sign-in method" tab and enable the Anonymous provider.

Firestore Database: Create a new database in Production mode.

Functions: Get started with the Functions service.

Register a new Web App in your project settings. Firebase will provide you with a firebaseConfig object. Copy this object.

2. ScraperAPI Setup
   Go to scraperapi.com and sign up for a free account.

From your ScraperAPI dashboard, copy your API Key.

3. Local Development Setup
   Clone this repository.

In the root directory, install the Firebase CLI if you haven't already: npm install -g firebase-tools.

Log in to Firebase: firebase login.

Initialize the project: firebase init. Select Firestore, Functions, and Hosting, and link it to the Firebase project you created.

Configure the Backend:

Navigate to the functions directory: cd functions.

Install dependencies: npm install axios cheerio.

Open functions/index.js and replace the placeholder YOUR_API_KEY with your actual key from ScraperAPI.

Configure the Frontend:

Navigate to the client directory: cd client.

Install dependencies: npm install.

Open src/App.js and replace the placeholder firebaseConfig object with the one you copied from your Firebase project.

Run the App:

From the client folder, start the React development server: npm start.

Your app will be running at http://localhost:3000.

4. Deployment to Firebase Hosting
   Build the React App: From the client directory, run npm run build. This creates a production-ready build in the client/build folder.

Deploy: Navigate to the root directory of the project and run the deploy command:

firebase deploy

This will deploy your Cloud Function, Firestore rules, and the contents of your client/build folder to Firebase Hosting. The command will output your live application URL.
