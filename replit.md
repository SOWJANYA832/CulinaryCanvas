# Bella Vista Restaurant Website

## Overview

This is a full-stack restaurant website built with React/TypeScript frontend and Express.js backend. The application serves as a landing page for "Bella Vista" restaurant, featuring a modern design with sections for menu display, about information, and contact form functionality.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **Styling**: Tailwind CSS with custom design system
- **UI Components**: Radix UI primitives with shadcn/ui component library
- **State Management**: React Query (@tanstack/react-query) for server state
- **Routing**: Wouter for lightweight client-side routing
- **Form Handling**: React Hook Form with Zod validation

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (@neondatabase/serverless)
- **Validation**: Zod schemas shared between frontend and backend
- **Session Management**: Express sessions with PostgreSQL store

### Database Schema
The application uses two main tables:
- **users**: For potential user authentication (username, password)
- **contacts**: For storing contact form submissions (name, email, phone, message, created_at)

## Key Components

### Frontend Components
1. **Navigation**: Fixed header with smooth scrolling navigation
2. **Hero**: Full-screen landing section with call-to-action buttons
3. **Menu**: Filterable menu items with category-based display
4. **About**: Restaurant information and chef profile
5. **Contact**: Contact form with validation and submission handling
6. **Footer**: Site footer with social links and quick navigation

### Backend Components
1. **Routes**: RESTful API endpoints for contact form and data retrieval
2. **Storage**: Abstracted storage layer with in-memory implementation for development
3. **Validation**: Shared Zod schemas for type safety across frontend and backend

## Data Flow

1. **Contact Form Submission**:
   - User fills out contact form on frontend
   - Form data validated using Zod schema
   - POST request sent to `/api/contact` endpoint
   - Backend validates and stores contact information
   - Success/error response returned to frontend
   - Toast notification displayed to user

2. **Menu Display**:
   - Static menu data stored in frontend
   - Client-side filtering by category
   - No backend interaction required

3. **Development vs Production**:
   - Development: Uses in-memory storage for quick testing
   - Production: Configured for PostgreSQL database with Drizzle ORM

## External Dependencies

### Frontend Dependencies
- **UI Framework**: React with extensive Radix UI component library
- **Styling**: Tailwind CSS with custom theme configuration
- **Icons**: Lucide React icons and React Icons
- **Fonts**: Google Fonts (Playfair Display, Inter, Dancing Script)
- **Images**: Unsplash for placeholder restaurant images

### Backend Dependencies
- **Database**: Neon PostgreSQL serverless database
- **ORM**: Drizzle ORM for type-safe database operations
- **Session Store**: connect-pg-simple for PostgreSQL session storage
- **Validation**: Shared Zod schemas for consistent validation

## Deployment Strategy

### Build Process
1. **Frontend**: Vite builds React app to `dist/public`
2. **Backend**: ESBuild bundles server code to `dist/index.js`
3. **Database**: Drizzle migrations applied via `db:push` command

### Environment Configuration
- **Development**: Uses Vite dev server with HMR and backend proxy
- **Production**: Serves static files from Express server
- **Database**: Requires `DATABASE_URL` environment variable

### Key Scripts
- `dev`: Development server with hot reload
- `build`: Production build for both frontend and backend
- `start`: Production server startup
- `db:push`: Apply database schema changes

The application follows a modern full-stack architecture with clear separation between frontend and backend concerns, shared type definitions, and a scalable database design suitable for a restaurant website's needs.