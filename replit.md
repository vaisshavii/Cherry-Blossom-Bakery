# Cherry Blossom Bakery - Replit.md

## Overview

This is a full-stack web application for Cherry Blossom Bakery, a vegetarian bakery in Rewa, MP. The application is built using a modern tech stack with React frontend, Express.js backend, and PostgreSQL database integration. The app features a product catalog with WhatsApp ordering integration and a beautiful, responsive UI using shadcn/ui components.

## User Preferences

Preferred communication style: Simple, everyday language.
Design preferences: Clean, professional look without excessive emojis; elegant cherry blossom theme with subtle gradients; product placeholders instead of emoji icons; sophisticated typography with serif fonts for headings.
Product requirements: 2x2 grid layout; exact individual pricing for each product variant; WhatsApp popup in bottom right corner; background image placeholder in header; comprehensive policies section; image gallery placeholders in product modals; ingredients information for each product; separate product entries for each flavor with individual pricing; ordering timeline (large orders: 2 days advance, small orders: 1 day advance).

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite with hot module replacement
- **UI Framework**: shadcn/ui components with Radix UI primitives
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **Routing**: Wouter for client-side routing
- **State Management**: TanStack React Query for server state management
- **Forms**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **API Style**: RESTful API endpoints
- **Database**: PostgreSQL with Drizzle ORM
- **Session Management**: Express sessions with PostgreSQL store
- **Development**: Hot reload with tsx

### Data Storage
- **Primary Database**: PostgreSQL (configured for Neon serverless)
- **ORM**: Drizzle with type-safe schema definitions
- **Migration Strategy**: Drizzle Kit for schema migrations
- **In-Memory Storage**: Fallback MemStorage class for development

## Key Components

### Database Schema (shared/schema.ts)
- **Products Table**: Stores bakery items with variants and pricing
- **Users Table**: Basic user authentication structure
- **Zod Integration**: Type-safe validation schemas

### Frontend Components
- **Product Modal**: Interactive product details with WhatsApp ordering
- **Floating Background**: Decorative UI element with emoji patterns
- **shadcn/ui Components**: Complete UI component library including dialogs, buttons, cards, etc.

### Backend Services
- **Product API**: RESTful endpoints for product catalog
- **Storage Interface**: Abstracted storage layer supporting both database and in-memory storage
- **Express Middleware**: Request logging, JSON parsing, error handling

### External Integrations
- **WhatsApp Business**: Direct ordering via WhatsApp links
- **Neon Database**: Serverless PostgreSQL hosting
- **Replit Integration**: Development environment optimization

## Data Flow

1. **Client Request**: Frontend makes API requests using TanStack Query
2. **Express Router**: Routes requests to appropriate handlers
3. **Data Layer**: Queries database using Drizzle ORM or fallback storage
4. **Response**: JSON data returned to frontend
5. **UI Update**: React components re-render with new data
6. **WhatsApp Integration**: External ordering flow via WhatsApp Business API

## External Dependencies

### Core Framework Dependencies
- React ecosystem (React, React DOM, React Query)
- Express.js with TypeScript support
- Drizzle ORM with PostgreSQL adapter

### UI/UX Dependencies
- Radix UI primitives for accessible components
- Tailwind CSS for styling
- Lucide React for icons
- Embla Carousel for image galleries

### Development Dependencies
- Vite for build tooling and development server
- TypeScript for type safety
- PostCSS with Autoprefixer

### Database Dependencies
- @neondatabase/serverless for PostgreSQL connection
- connect-pg-simple for session storage
- Drizzle Kit for migrations

## Deployment Strategy

### Development Environment
- **Development Server**: Vite dev server with HMR
- **Backend**: tsx for TypeScript execution with hot reload
- **Database**: Development database with automatic schema push

### Production Build
- **Frontend Build**: Vite production build with optimizations
- **Backend Build**: esbuild for Node.js bundle creation
- **Static Assets**: Served from dist/public directory
- **Process Management**: Single Node.js process serving both API and static files

### Environment Configuration
- **DATABASE_URL**: PostgreSQL connection string (required)
- **NODE_ENV**: Environment detection (development/production)
- **Session Configuration**: PostgreSQL-backed sessions for scalability

### Key Architectural Decisions

1. **Monorepo Structure**: Single repository with client, server, and shared code for easier development and deployment
2. **Type Safety**: End-to-end TypeScript with shared schema definitions
3. **Database Abstraction**: Storage interface allows for easy switching between database and in-memory storage
4. **Component Library**: shadcn/ui provides consistent, accessible UI components
5. **API Design**: Simple REST endpoints with proper error handling and logging
6. **WhatsApp Integration**: External ordering system reduces complexity while providing familiar user experience
7. **Responsive Design**: Mobile-first approach with Tailwind CSS utilities