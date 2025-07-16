# replit.md

## Overview

This is a full-stack web application built with React (TypeScript) frontend and Express.js backend. The application is a professional portfolio website for a UI designer named "Kirin" who specializes in Roblox UI design with 4+ years of experience. The portfolio showcases authentic work from games including Da Bronx, Da Hood Remake, South London 2, and Miami Remastered. The application includes a contact form system with database integration using Drizzle ORM and PostgreSQL.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **Styling**: Tailwind CSS with custom design system
- **UI Components**: Radix UI primitives with shadcn/ui component library
- **State Management**: TanStack Query (React Query) for server state
- **Routing**: Wouter for lightweight client-side routing
- **Animations**: Framer Motion for smooth transitions and interactions

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (@neondatabase/serverless)
- **API Pattern**: RESTful API with JSON responses
- **Error Handling**: Centralized error middleware
- **Development**: Hot reload with Vite integration

### Development Setup
- **Monorepo Structure**: Client, server, and shared code in single repository
- **TypeScript**: Strict configuration with path mapping
- **ESM**: Full ES modules support throughout the stack
- **Development Server**: Vite dev server with Express API proxy

## Key Components

### Database Schema (`shared/schema.ts`)
- **contacts** table with fields: id, name, email, projectType, message, createdAt
- Zod validation schemas for type safety
- Drizzle ORM with PostgreSQL dialect

### API Endpoints (`server/routes.ts`)
- `POST /api/contacts` - Create new contact submission
- `GET /api/contacts` - Retrieve all contacts
- Input validation using Zod schemas
- Error handling for validation and database errors

### Storage Layer (`server/storage.ts`)
- Interface-based design for storage abstraction
- Currently using in-memory storage (MemStorage class)
- Designed to be easily switched to database implementation

### UI Components
- **Navigation**: Responsive navigation with smooth scrolling
- **Hero Section**: Animated landing section with call-to-action
- **Portfolio**: Project showcase with visual cards
- **Skills**: Progress bars and skill demonstrations
- **Contact Form**: Validated form with project type selection
- **Responsive Design**: Mobile-first approach with Tailwind CSS

### Form Handling
- React Hook Form with Zod validation
- TanStack Query for API mutations
- Toast notifications for user feedback
- Form state management and error handling

## Data Flow

1. **Contact Form Submission**:
   - User fills out contact form (name, email, project type, message)
   - Client-side validation with Zod schemas
   - Form data sent to `/api/contacts` endpoint
   - Server validates and stores data
   - Success/error feedback via toast notifications

2. **Contact Data Retrieval**:
   - Admin can potentially view submitted contacts via `/api/contacts`
   - Data sorted by creation date (newest first)

3. **Static Content**:
   - Portfolio sections are statically rendered
   - Smooth scrolling navigation between sections
   - Responsive design adapts to different screen sizes

## External Dependencies

### Frontend Dependencies
- **UI Framework**: React, React DOM
- **Styling**: Tailwind CSS, PostCSS, Autoprefixer
- **UI Components**: Radix UI primitives, shadcn/ui components
- **Animation**: Framer Motion
- **Form Handling**: React Hook Form, Hookform Resolvers
- **HTTP Client**: TanStack Query for API calls
- **Routing**: Wouter for client-side routing
- **Utilities**: clsx, class-variance-authority, date-fns

### Backend Dependencies
- **Server**: Express.js
- **Database**: Drizzle ORM, @neondatabase/serverless
- **Validation**: Zod, drizzle-zod
- **Session**: connect-pg-simple (for PostgreSQL sessions)
- **Development**: tsx for TypeScript execution

### Development Tools
- **Build**: Vite, esbuild
- **TypeScript**: Full type checking and compilation
- **Database**: Drizzle Kit for migrations and schema management
- **Replit Integration**: Runtime error overlay and development banner

## Deployment Strategy

### Build Process
1. **Frontend Build**: Vite builds React app to `dist/public`
2. **Backend Build**: esbuild bundles server code to `dist/index.js`
3. **Static Assets**: Client assets served from `dist/public`

### Production Configuration
- **Environment**: NODE_ENV=production
- **Database**: PostgreSQL connection via DATABASE_URL
- **Static Serving**: Express serves built React app
- **API Routes**: Prefixed with `/api/`

### Development vs Production
- **Development**: Vite dev server with HMR, Express API proxy
- **Production**: Express serves static files and API routes
- **Database**: Drizzle migrations managed via `db:push` command

### Database Management
- **Migrations**: Stored in `./migrations` directory
- **Schema**: Defined in `shared/schema.ts`
- **Connection**: PostgreSQL via environment variable
- **ORM**: Drizzle ORM with type-safe queries

The application is structured as a modern full-stack TypeScript application with clear separation of concerns, type safety throughout, and a scalable architecture that can easily be extended with additional features.