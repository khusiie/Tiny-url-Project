# 🔗 TinyLink - URL Shortener

TinyLink is a modern, full-stack URL shortening application that allows users to create short, memorable links from long URLs. Built with Next.js and Express, it features click tracking, custom short codes, and a clean, responsive interface.

---

## Table of Contents

- [Features](#-features)  
- [Tech Stack](#-tech-stack)  
- [Project Structure](#-project-structure)  
- [Getting Started](#-getting-started)  
- [API Endpoints](#-api-endpoints)  
- [Deployment](#-deployment)  
- [How It Works](#-how-it-works)  

---

## Features

- **URL Shortening**: Convert long URLs into short, shareable links  
- **Custom Short Codes**: Create personalized short codes or use auto-generated ones  
- **Click Tracking**: Monitor how many times each link has been clicked  
- **Link Management**: View all your links in a dashboard with creation dates  
- **Auto-Redirect**: Seamlessly redirect users from short links to original URLs  
- **Responsive Design**: Modern UI built with Tailwind CSS that works on all devices  
- **Real-time Stats**: Track last clicked timestamp and total clicks per link  
- **Delete Links**: Remove links you no longer need  

---

##  Tech Stack

**Frontend (Client)**

- Next.js 16 - React framework with App Router  
- React 19 - UI library  
- TypeScript - Type safety  
- Tailwind CSS v4 - Utility-first CSS framework  
- Axios - HTTP client for API requests  
- Lucide React - Modern icon library  
- date-fns - Date formatting utilities  

**Backend (Server)**

- Node.js - JavaScript runtime  
- Express.js v5 - Web application framework  
- MongoDB - NoSQL database  
- Mongoose v9 - MongoDB object modeling  
- nanoid - Unique ID generator  
- CORS - Cross-origin resource sharing  
- dotenv - Environment variable management  

---

##  Project Structure
tinylink/
├── client/ # Next.js frontend application
│ ├── src/
│ │ ├── app/ # Next.js App Router pages
│ │ │ ├── page.tsx # Main dashboard page
│ │ │ ├── layout.tsx # Root layout
│ │ │ ├── globals.css
│ │ │ └── code/ # Stats page for individual links
│ │ └── lib/ # Utility functions
│ ├── public/ # Static assets
│ ├── package.json
│ └── next.config.ts
│
├── server/ # Express.js backend API
│ ├── config/ # Database configuration
│ ├── models/ # Mongoose schemas
│ │ └── Link.js # Link model (code, originalUrl, clicks, etc.)
│ ├── routes/ # API route handlers
│ │ └── linkRoutes.js # CRUD operations for links
│ ├── server.js # Express app entry point
│ ├── package.json
│ └── .env # Environment variables
│
├── deployment.md # Deployment instructions
└── README.md # This file


---

## Getting Started

### Prerequisites

- Node.js (v18 or higher)  
- MongoDB (local installation or MongoDB Atlas account)  
- npm or yarn  

### Installation

**Clone the repository**

```bash
git clone <your-repo-url>
cd tinylink
Set up the Server

cd server
npm install


Create a .env file in the server directory:

MONGO_URI=your_mongodb_connection_string
PORT=5000


Set up the Client

cd ../client
npm install


Create a .env.local file in the client directory:

NEXT_PUBLIC_API_URL=http://localhost:5000

Running Locally

Start the Server (from server directory):

npm run dev


Server runs on http://localhost:5000

Start the Client (from client directory):

npm run dev

Client runs on http://localhost:3000

## API Endpoints

Base URL: /api/links

Method	Endpoint	Description	Request Body
POST	/api/links	Create a new short link	{ originalUrl: string, customCode?: string }
GET	/api/links	Get all links (sorted by newest)	-
GET	/api/links/:code	Get a specific link by code	-
DELETE	/api/links/:code	Delete a link by code	-

Redirection Endpoint

Method	Endpoint	Description
GET	/:code	Redirect to original URL and increment click count

Health Check

Method	Endpoint	Description
GET	/healthz	Server health check

## Deployment

Frontend: Vercel (recommended for Next.js)

Backend: Render (free tier available)

Database: MongoDB Atlas (free tier available)

See deployment.md for detailed deployment instructions.

## How It Works
Database Schema (Link Model)
{
  "code": "abc123",           // Unique short code
  "originalUrl": "https://example.com", // Full URL
  "clicks": 0,                // Click count
  "lastClickedAt": null,      // Last clicked timestamp
  "createdAt": "2025-01-01T00:00:00Z"
}

## Workflow

User submits a URL on the dashboard

Server generates a unique 6-character code (or uses custom code)

Link is stored in MongoDB

User receives a shortened URL (e.g., https://yourdomain.com/abc123)

When visited, the server:

Looks up the code in the database

Increments the click counter

Updates the lastClickedAt timestamp

Redirects to the original URL

## Key Features Implementation

Unique Code Generation: Uses a random character generator with collision checking

Custom Codes: Users can specify their own short codes (validated for uniqueness)

Click Tracking: Automatically incremented on each redirect

Error Handling: Validates URLs, handles 404s for non-existent codes

CORS Enabled: Frontend and backend can run on different domains

## License

This project is open source and available for educational purposes.

## Contributing

Feel free to fork this project and submit pull requests for improvements!
---



