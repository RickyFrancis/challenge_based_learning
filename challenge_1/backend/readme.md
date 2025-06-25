# 🐱 Backend Challenge: PurrfectMatch - European Cat Adoption Platform

## 🎯 Project Overview

You're building the backend for **PurrfectMatch**, a platform that connects cat lovers across the European Union. This platform facilitates cat adoption and community building while handling basic EU-specific regulations.

## 🏗️ Architecture & Tech Stack

- **Runtime**: Node.js 18+
- **Framework**: Hono.js
- **Language**: TypeScript (strict mode)
- **API**: GraphQL with Apollo Server
- **Database**: PostgreSQL with Prisma ORM
- **Authentication**: JWT with refresh tokens + Cookie-based auth
- **File Storage**: Cloudflare R2 or AWS S3
- **Testing**: Jest + Supertest
- **Documentation**: GraphQL Playground
- **Containerization**: Docker + Docker Compose
- **Caching**: Redis (containerized)

## 🐳 Docker Requirements

### Multi-Container Architecture

Your application must be containerized with these core services:

1. **API Service**: Node.js application container
2. **Database**: PostgreSQL container
3. **Cache**: Redis container
4. **AI Service**: Dedicated container for AI operations (Week 2)

### Docker Setup Requirements

#### Development Environment

- [ ] Create `Dockerfile` for the main API service
- [ ] Set up `docker-compose.yml` for local development
- [ ] Include volume mounts for code changes and database persistence
- [ ] Configure environment variables through `.env` files
- [ ] Set up basic health checks

#### Production Environment

- [ ] Create optimized `Dockerfile` for production builds
- [ ] Set up `docker-compose.prod.yml` for production deployment
- [ ] Configure proper logging

### Docker Best Practices

- [ ] Use specific version tags for base images
- [ ] Run containers as non-root users
- [ ] Minimize image size (target < 300MB for API service)
- [ ] Use `.dockerignore` to exclude unnecessary files

## 🎯 Core Features

### 1. User Management & Authentication

- User registration with email verification
- **Dual Authentication**: JWT-based + Cookie-based authentication
- **Session Management**: Secure HTTP-only cookies with CSRF protection
- **Refresh Token Strategy**: Implement refresh token rotation
- Role-based access (Adopter, Breeder, Admin)
- Profile management with EU country validation

### 2. Cat Listings & Management

- Cat profiles with photos and basic information
- Breed information
- Health records and vaccination status
- Adoption vs. Sale categorization

### 3. Basic EU Compliance

- Country-specific adoption requirements (3-5 countries)
- Basic insurance requirement validation
- Microchip validation

### 4. Search & Discovery

- Basic search and filtering
- Location-based search with EU country filtering
- Pagination and sorting

### 5. Community Features

- Basic messaging system between users
- User reviews and ratings

### 6. AI Integration (The Tricky Part!)

- **Cat Health Assessment**: Implement an AI service that analyzes uploaded cat photos to detect potential health issues and breed identification
- Expose this as a GraphQL mutation: `analyzeCatHealth(imageUrl: String!): CatHealthAnalysis`
- Use a pre-trained model or integrate with services like Google Vision AI
- Implement basic rate limiting
- **Containerized AI Service**: Run AI operations in a separate container

## 🚀 Challenge Phases (2 Weeks)

### Week 1: Foundation & Core Features

#### Phase 1.1: Project Setup & Dockerization (Days 1-2)

- [ ] Initialize Hono.js project with TypeScript
- [ ] Set up GraphQL with Apollo Server integration
- [ ] Configure Prisma with PostgreSQL
- [ ] **Implement dual authentication system (JWT + Cookies)**
- [ ] **Set up session management with Redis**
- [ ] Set up testing framework with Jest
- [ ] **Create Dockerfile for API service**
- [ ] **Set up docker-compose.yml for local development**
- [ ] **Configure PostgreSQL and Redis containers**

#### Phase 1.2: Database Design & Models (Days 3-4)

- [ ] Design database schema for core entities
- [ ] Implement Prisma models for users, cats, and basic features
- [ ] Create database migrations
- [ ] Set up seed data for testing
- [ ] **Configure database container with proper volumes**

#### Phase 1.3: Core API Development (Days 5-7)

- [ ] Implement user management endpoints
- [ ] **Create authentication middleware for both JWT and cookies**
- [ ] **Implement session management and CSRF protection**
- [ ] Create cat listing CRUD operations
- [ ] Build basic search and filtering capabilities
- [ ] Implement file upload for images
- [ ] Add pagination and sorting
- [ ] Create GraphQL resolvers with proper error handling

### Week 2: Advanced Features & Polish

#### Phase 2.1: EU Compliance & Legal Features (Days 8-9)

- [ ] Implement basic country-specific validation rules (3-5 countries)
- [ ] Create insurance requirement endpoints
- [ ] Build microchip validation system
- [ ] Add vaccination tracking

#### Phase 2.2: AI Integration & Advanced Features (Days 10-11)

- [ ] Implement cat health analysis AI service
- [ ] **Create dedicated AI service container**
- [ ] Add basic messaging system
- [ ] Implement user reviews and ratings

#### Phase 2.3: Testing & Documentation (Days 12-13)

- [ ] Write unit tests (70%+ coverage)
- [ ] Create integration tests for main endpoints
- [ ] **Create Docker-based testing environment**
- [ ] Write API documentation
- [ ] Create deployment documentation

#### Phase 2.4: Deployment & Final Polish (Day 14)

- [ ] **Create production Docker images**
- [ ] **Set up docker-compose.prod.yml**
- [ ] Deploy to production environment
- [ ] Basic security audit
- [ ] Final testing and bug fixes
- [ ] Prepare handoff documentation

## 🎯 Tricky Requirements & Real-World Caveats

### 1. Multi-Country EU Compliance

- Handle different VAT rates per EU country
- Implement country-specific adoption laws (focus on 3-5 major countries)
- Manage different currency formats
- Handle timezone differences

### 2. Search & Filtering

- Implement basic full-text search with PostgreSQL
- Handle multiple language support (EN, DE, FR)
- Create filtering with multiple criteria
- Handle performance with basic indexing

### 3. File Upload & Media Management

- Implement secure file upload with validation
- Handle multiple image formats
- Basic image optimization
- Implement CDN integration

### 4. Security Challenges

- Implement rate limiting per endpoint
- Add CSRF protection for cookie-based auth
- **Implement secure cookie settings (HttpOnly, Secure, SameSite)**
- **Handle session invalidation and cleanup**
- Handle SQL injection prevention
- Implement proper input validation
- Add security headers and CORS configuration

### 5. Docker-Specific Challenges

- **Handle container orchestration**
- **Manage persistent data across container restarts**
- **Implement proper logging**
- **Handle container networking**

## 📋 Technical Requirements

### Code Quality Standards

- **TypeScript**: Strict mode enabled, no `any` types
- **ESLint**: Airbnb config with custom rules
- **Prettier**: Consistent code formatting
- **Commit Convention**: Conventional commits format

### Performance Requirements

- API response time < 300ms for 95% of requests
- Support 500+ concurrent users
- Database queries optimized with basic indexing
- Implement caching strategy (Redis)
- Handle file uploads up to 20MB

### Testing Requirements

- **Unit Tests**: 70%+ code coverage
- **Integration Tests**: Main API endpoints
- **Container Tests**: Test services in Docker environment

### Documentation Requirements

- **GraphQL Schema**: Self-documenting with descriptions
- **API Documentation**: Basic OpenAPI/Swagger spec
- **README**: Setup and deployment guide
- **Docker Documentation**: Container setup guide

## 🎯 AI Integration Specifics

### Cat Health Analysis Service

- **Input**: Cat photo URL
- **Output**: Health assessment, breed identification
- **Implementation**:
  - Use Google Vision AI or Azure Computer Vision
  - Implement basic image preprocessing
  - Create confidence scoring
  - Handle basic edge cases
  - **Run in dedicated container**
- **GraphQL Schema**:

```graphql
type CatHealthAnalysis {
  healthScore: Float!
  breedPrediction: [BreedPrediction!]!
  healthIssues: [HealthIssue!]!
  confidence: Float!
  analysisDate: DateTime!
}

type BreedPrediction {
  breed: String!
  confidence: Float!
}

type HealthIssue {
  issue: String!
  severity: HealthSeverity!
  description: String!
}

type AuthResponse {
  user: User!
  token: String
  sessionId: String
  expiresAt: DateTime!
}

type LoginInput {
  email: String!
  password: String!
  authMethod: AuthMethod! # JWT or COOKIE
}

enum AuthMethod {
  JWT
  COOKIE
}
```

## 🚀 Deployment & DevOps

### Environment Setup

- **Development**: Local with Docker Compose
- **Production**: Docker containers on VPS or cloud platform
- **Database**: Containerized PostgreSQL with persistent volumes

### Docker Deployment Options

- **Local Development**: `docker-compose up`
- **VPS Deployment**: Docker Compose
- **CI/CD**: Basic automated Docker builds

### Monitoring & Observability

- **Error Tracking**: Basic Sentry integration
- **Logging**: Structured logging with Winston
- **Health Checks**: Basic endpoint monitoring

## 📊 Success Criteria

### Functional Requirements

- [ ] All core features implemented and working
- [ ] AI integration functional and exposed via GraphQL
- [ ] EU compliance features working for 3-5 countries
- [ ] File upload and media management operational
- [ ] **All services running in Docker containers**

### Non-Functional Requirements

- [ ] API response times meet performance targets
- [ ] Test coverage exceeds 70%
- [ ] Basic security audit passes
- [ ] Documentation is complete
- [ ] **Docker images are optimized**

### Quality Gates

- [ ] All tests passing in CI/CD
- [ ] Code review completed
- [ ] Basic performance benchmarks met
- [ ] **Docker security scan passed**
- [ ] **Container health checks passing**

## 🎯 Bonus Challenges (Optional)

1. **Multi-language Support**: Implement i18n for 3+ EU languages
2. **Payment Integration**: Add Stripe for premium features
3. **Real-time Features**: Add WebSocket for messaging
4. **Advanced Caching**: Implement Redis for session management
5. **Background Jobs**: Add queue system for heavy operations
6. **Kubernetes Deployment**: Set up basic K8s manifests

## 📚 Learning Resources

- [Hono.js Documentation](https://hono.dev/)
- [GraphQL with Apollo Server](https://www.apollographql.com/docs/apollo-server/)
- [Prisma ORM](https://www.prisma.io/docs/)
- [TypeScript Best Practices](https://www.typescriptlang.org/docs/)
- [PostgreSQL Performance](https://www.postgresql.org/docs/current/performance.html)
- [Jest Testing Framework](https://jestjs.io/docs/getting-started)
- [Docker Best Practices](https://docs.docker.com/develop/dev-best-practices/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)

## 🎯 Handoff Checklist

Before handing off to the frontend developer, ensure:

- [ ] All GraphQL endpoints are documented
- [ ] **Authentication flow is clearly documented (both JWT and Cookie methods)**
- [ ] **Session management and CSRF protection are documented**
- [ ] Error codes and messages are standardized
- [ ] API rate limits are documented
- [ ] File upload specifications are clear
- [ ] Environment variables are documented
- [ ] **Docker setup is documented and working**
- [ ] **All services can be started with `docker-compose up`**

## 🐳 Docker File Structure

```
project/
├── docker-compose.yml
├── docker-compose.prod.yml
├── Dockerfile
├── Dockerfile.ai
├── .dockerignore
├── docker/
│   ├── postgres/
│   └── redis/
└── scripts/
    ├── docker-build.sh
    └── docker-deploy.sh
```

---

**Remember**: This is a real-world project that will be used in portfolios. Focus on clean architecture, proper error handling, comprehensive testing, and professional containerization. The AI integration should be a nice-to-have feature that enhances the user experience, not the core functionality.

**Goal**: Complete the project successfully rather than being overwhelmed. Start with core features and add complexity gradually.

Good luck! 🚀
