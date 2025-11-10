# ShopCraft E-Commerce Platform - Technical Architecture

## Overview
ShopCraft is a modern e-commerce platform built with a focus on performance, user experience, and scalability. The application follows a clean architecture with separated frontend and backend concerns.

## Technology Stack

### Frontend
- **React 18** with TypeScript for type safety and modern development
- **React Router** for client-side navigation
- **Tailwind CSS** for utility-first styling and responsive design
- **Vite** for fast development and optimized builds
- **Context API + Custom Hooks** for state management

### Backend
- **Hono** - Fast, lightweight web framework for Cloudflare Workers
- **Cloudflare Workers** for serverless edge computing
- **TypeScript** for type safety across the entire stack

### Database
- **Cloudflare D1** (SQLite-based) for relational data storage
- **Optimized for serverless** with minimal cold start times

### Development & Build Tools
- **ESLint + TypeScript ESLint** for code quality
- **Bun** for package management and fast builds
- **Wrangler** for Cloudflare Workers deployment

## Architecture Components

### 1. Frontend Architecture

#### Component Structure
```
src/react-app/
├── components/          # Reusable UI components
│   ├── Header.tsx      # Navigation and cart access
│   ├── CartDrawer.tsx  # Shopping cart sidebar
│   └── ProductCard.tsx # Product display component
├── pages/              # Route-level components
│   ├── Home.tsx        # Product catalog and search
│   └── ProductDetail.tsx # Individual product view
├── hooks/              # Custom React hooks
│   └── useCart.tsx     # Shopping cart state management
└── App.tsx            # Main application component
```

#### State Management
- **Cart State**: Managed through React Context with persistent session storage
- **Product Data**: Fetched from API and cached in component state
- **Session Management**: Browser localStorage for cart persistence

#### Key Features
- **Responsive Design**: Mobile-first approach with Tailwind CSS
- **Real-time Cart Updates**: Optimistic updates with error handling
- **Search & Filter**: Client-side filtering with category support
- **Product Discovery**: Featured products section and catalog view

### 2. Backend Architecture

#### API Structure
```
src/worker/
└── index.ts           # Hono app with all API routes
```

#### API Endpoints
```
GET  /api/products           # List all products
GET  /api/products/:id       # Get single product
GET  /api/cart              # Get cart items for session
POST /api/cart              # Add item to cart
PUT  /api/cart/:id          # Update cart item quantity
DELETE /api/cart/:id        # Remove cart item
```

#### Session Management
- **Session ID Generation**: Client-generated UUID stored in localStorage
- **Session Validation**: Passed via `x-session-id` header
- **Cart Persistence**: Server-side storage tied to session ID

### 3. Database Schema

#### Products Table
```sql
CREATE TABLE products (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT NOT NULL,
  description TEXT,
  price REAL NOT NULL,
  image_url TEXT,
  category TEXT,
  stock_quantity INTEGER DEFAULT 0,
  is_featured BOOLEAN DEFAULT 0,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### Cart Items Table
```sql
CREATE TABLE cart_items (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  session_id TEXT NOT NULL,
  product_id INTEGER NOT NULL,
  quantity INTEGER NOT NULL DEFAULT 1,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### Indexes for Performance
- Products: `category`, `is_featured`
- Cart Items: `session_id`, `product_id`

### 4. Type Safety

#### Shared Types (Zod Schemas)
```typescript
// All data types validated with Zod for runtime safety
export const ProductSchema = z.object({...});
export const CartItemSchema = z.object({...});
export const AddToCartSchema = z.object({...});
```

#### Benefits
- **Runtime Validation**: API request/response validation
- **Type Inference**: Automatic TypeScript types from Zod schemas
- **Error Handling**: Structured validation errors

## Security Considerations

### Data Protection
- **Input Validation**: All API inputs validated with Zod schemas
- **SQL Injection Prevention**: Parameterized queries only
- **Session Isolation**: Cart data isolated by session ID

### Performance Optimizations
- **Edge Computing**: Cloudflare Workers for global distribution
- **Optimized Queries**: Efficient database queries with proper indexes
- **Image Optimization**: External image URLs with CDN delivery
- **Bundle Optimization**: Tree-shaking and code splitting with Vite

## Deployment Architecture

### Production Environment
- **Frontend**: Static assets served by Cloudflare Pages
- **Backend**: Cloudflare Workers for API endpoints
- **Database**: Cloudflare D1 for data persistence
- **CDN**: Cloudflare CDN for global content delivery

### Development Environment
- **Local Development**: Vite dev server with HMR
- **Database**: Local SQLite instance
- **API Testing**: Built-in Hono testing capabilities

## Scalability Considerations

### Horizontal Scaling
- **Serverless Architecture**: Auto-scaling Workers
- **Database**: D1 handles high-concurrency reads
- **CDN**: Global edge distribution

### Performance Monitoring
- **Error Tracking**: Structured error handling
- **Performance Metrics**: Core Web Vitals optimization
- **Database Monitoring**: Query performance tracking

## Development Workflow

### Code Organization
- **Separation of Concerns**: Clear frontend/backend boundaries
- **Type Safety**: End-to-end TypeScript coverage
- **Code Quality**: ESLint rules and consistent formatting

### Testing Strategy
- **Type Safety**: Compile-time error prevention
- **API Validation**: Runtime schema validation
- **Manual Testing**: Comprehensive user flow testing

This architecture provides a solid foundation for a modern e-commerce platform with excellent performance, maintainability, and user experience.
