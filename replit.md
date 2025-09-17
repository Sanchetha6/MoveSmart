# MoveSmart - AI Traffic Management System

## Overview

This is a comprehensive traffic management system that uses computer vision and real-time data processing to optimize traffic flow at intersections. The system consists of a React frontend with a TypeScript Express backend, integrated with Python-based computer vision for vehicle detection, and features real-time WebSocket communication for live traffic updates.

The application provides two main interfaces: a comprehensive dashboard for traffic operators and a commuter-facing app for route optimization. It uses AI-powered vehicle detection to identify emergency vehicles and automatically adjust traffic light timing to prioritize emergency response while optimizing overall traffic flow.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

The client application is built with React and TypeScript, using Vite for build tooling and development. It follows a modern component-based architecture with:

- **UI Framework**: Radix UI components with shadcn/ui styling system for consistent, accessible interfaces
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query for server state management and caching
- **Styling**: Tailwind CSS with custom design tokens and CSS variables for theming
- **Real-time Updates**: Custom WebSocket hooks for live traffic data synchronization

The frontend is organized into distinct pages (dashboard, commuter app) with reusable components for metrics display, intersection tables, video feeds, and traffic control panels.

### Backend Architecture

The server uses Express.js with TypeScript in ESM format, implementing a service-oriented architecture:

- **API Layer**: RESTful endpoints for CRUD operations on intersections, camera feeds, emergency alerts, and traffic metrics
- **Real-time Communication**: WebSocket server for broadcasting live updates to connected clients
- **Service Layer**: 
  - CVProcessor service for computer vision integration with Python scripts
  - TrafficOptimizer service implementing rule-based traffic light optimization algorithms
- **Storage Layer**: Abstracted storage interface with in-memory implementation, designed for easy database integration

### Data Storage Solutions

The system uses Drizzle ORM with PostgreSQL for data persistence, featuring:

- **Schema Design**: Well-defined tables for intersections, camera feeds, emergency alerts, and traffic metrics
- **Type Safety**: Drizzle-Zod integration for runtime validation and TypeScript type generation
- **Migration Support**: Drizzle Kit for database schema migrations
- **Connection**: Neon Database serverless PostgreSQL for cloud deployment

Key entities include intersections with traffic light states, camera feeds with detected vehicle data, emergency alerts with priority levels, and comprehensive traffic metrics for analytics.

### Computer Vision Integration

Python-based vehicle detection system using OpenCV:

- **Detection Engine**: YOLO-based object detection for vehicle identification and classification
- **Emergency Vehicle Recognition**: Specialized detection for ambulances, fire trucks, and police vehicles
- **Processing Pipeline**: Spawned Python processes communicate with Node.js backend via JSON
- **Real-time Analysis**: Continuous video feed processing with bounding box detection and confidence scoring

### Traffic Optimization Engine

Rule-based optimization system that processes traffic data to make intelligent decisions:

- **Optimization Rules**: Configurable rules for high traffic extension, low traffic early switching, emergency vehicle priority, and traffic coordination
- **Priority System**: Hierarchical priority levels ensuring emergency vehicles get immediate precedence
- **Dynamic Timing**: Adaptive traffic light timing based on real-time vehicle counts and wait times
- **Coordination Logic**: Inter-intersection coordination for traffic flow optimization

## External Dependencies

### Core Framework Dependencies
- **React 18**: Frontend framework with modern concurrent features
- **Express.js**: Backend web framework for API and WebSocket services
- **TypeScript**: Type safety across the entire application stack
- **Vite**: Frontend build tool with HMR and optimized production builds

### Database and ORM
- **Drizzle ORM**: Type-safe database toolkit with PostgreSQL support
- **Neon Database**: Serverless PostgreSQL hosting (@neondatabase/serverless)
- **Drizzle Kit**: Database migration and schema management tools

### UI and Styling
- **Radix UI**: Comprehensive set of accessible React components
- **Tailwind CSS**: Utility-first CSS framework for rapid styling
- **shadcn/ui**: Pre-built component library built on Radix UI and Tailwind
- **Lucide React**: Icon library for consistent iconography

### State Management and Data Fetching
- **TanStack Query**: Server state management with caching and synchronization
- **React Hook Form**: Form state management with validation
- **Zod**: Runtime type validation and schema parsing

### Real-time Communication
- **WebSocket (ws)**: Native WebSocket implementation for real-time updates
- **Custom WebSocket hooks**: React hooks for managing WebSocket connections and state

### Computer Vision
- **OpenCV Python**: Computer vision library for image and video processing
- **NumPy**: Numerical computing library for array operations
- **YOLO**: Object detection model for vehicle identification

### Development and Build Tools
- **ESBuild**: Fast JavaScript bundler for production builds
- **TSX**: TypeScript execution environment for development
- **PostCSS**: CSS post-processing with Autoprefixer
- **Replit Integration**: Development environment plugins and error overlays