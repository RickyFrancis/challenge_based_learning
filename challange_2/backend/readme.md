# �� Backend Challenge: Spirited - The Social Catalog for Drinks & Spirits

## Assigned to Ricky Francis Rozario

## 🎯 Project Overview

You're building the backend for **Spirited**, a community-driven platform for hobbyist bartenders and drink enthusiasts. Like Fragrantica for perfumes, Spirited is a place to discover, catalog, review, and share experiences with cocktails, spirits, liqueurs, and ingredients. Users can rate drinks, write tasting notes, build personal collections, and connect with others who share their taste.

## 🏗️ Architecture & Tech Stack

- **Runtime**: Node.js 18+ with TypeScript
- **Framework**: Koa.js
- **API**: RESTful API with comprehensive Postman documentation
- **Database**: PostgreSQL with Prisma ORM
- **Authentication**: JWT with refresh tokens
- **Testing**: Jest + Supertest
- **Documentation**: Postman Collections with detailed examples
- **Containerization**: Docker + Docker Compose
- **CI/CD**: GitHub Actions
- **Caching**: Redis (sessions and trending data)

## 🐳 Docker Requirements

### Multi-Container Architecture

Your application must be containerized with these core services:

1. **API Service**: Koa.js application container
2. **Database**: PostgreSQL container
3. **Cache**: Redis container
4. **Analytics Service**: Container for trending and stats (Week 2)

## 🎯 Core Features

### 1. User Management & Authentication

- User registration with email verification
- Social login (Google, Facebook)
- Profile with avatar, bio, and favorite drink styles
- Session management (JWT + Redis)

### 2. Drink & Ingredient Catalog

- Community-driven catalog of cocktails, spirits, liqueurs, and mixers
- Detailed pages for each drink/ingredient (origin, ABV, flavor notes, etc.)
- Tagging system (e.g., "fruity", "smoky", "herbal", "sweet", "bitter")
- Add new drinks/ingredients (with moderation)

### 3. Reviews, Ratings & Tasting Notes

- Users can rate and review drinks/ingredients
- Write detailed tasting notes (aroma, taste, finish, etc.)
- Like and comment on others' reviews
- Aggregate ratings and trending drinks

### 4. Collections, Wishlists & Social Features

- Users can create personal collections ("Tried", "Wishlist", "Favorites")
- Follow other users and see their collections/reviews
- Activity feed (who reviewed what, new drinks added, etc.)
- Share collections or reviews via public links

### 5. Discovery & Search

- Advanced search and filtering (by style, ABV, tags, rating, etc.)
- Trending and top-rated drinks
- Personalized recommendations ("Because you liked...")
- Random drink/ingredient suggestion

## 🚀 Challenge Phases (2 Weeks)

### Week 1: Foundation & Core Features

- [ ] Initialize Koa.js project with TypeScript
- [ ] Set up PostgreSQL with Prisma ORM
- [ ] Configure Redis for caching and sessions
- [ ] Implement authentication and user profiles
- [ ] Create Dockerfile and docker-compose.yml
- [ ] Design database schema for users, drinks, ingredients, reviews, collections
- [ ] Implement endpoints for catalog browsing and user registration/login
- [ ] Set up testing framework with Jest

### Week 2: Social, Discovery & Polish

- [ ] Implement reviews, ratings, and tasting notes
- [ ] Add collections, wishlists, and social following
- [ ] Build advanced search and trending endpoints
- [ ] Add activity feed and sharing features
- [ ] Write unit and integration tests (80%+ coverage)
- [ ] Set up GitHub Actions CI/CD pipeline
- [ ] Complete Postman collection with all endpoints
- [ ] Polish API documentation and deployment scripts

## 🎯 Tricky Requirements & Real-World Caveats

- Prevent duplicate drinks/ingredients (fuzzy matching, moderation)
- Handle subjective reviews and rating aggregation fairly
- Support for non-English drink names and internationalization
- Efficiently cache trending and top-rated lists (Redis)
- Privacy controls for collections (public/private)
- Rate limiting and abuse prevention for reviews/comments

## 📋 Technical Requirements

- **TypeScript**: Strict mode, no `any` types
- **ESLint**: Airbnb config
- **Prettier**: Consistent formatting
- **Commit Convention**: Conventional commits
- **Code Coverage**: 80%+ for unit tests
- **API Response Time**: <200ms for 95% of requests
- **Support**: 1000+ concurrent users
- **Testing**: Unit, integration, and performance tests
- **CI/CD**: GitHub Actions for test/build/deploy
- **Documentation**: Postman collections, README, Docker setup

## 📝 Postman Documentation Requirements

### Collection Structure

1. **Authentication**
   - Register
   - Login (JWT)
   - Social Login
   - Refresh Token
2. **User Profile**
   - Get/Update Profile
   - Avatar Upload
   - Follow/Unfollow User
3. **Drinks & Ingredients**
   - List/Search Drinks
   - Get Drink Details
   - Add/Edit Drink (with moderation)
   - List/Search Ingredients
   - Get Ingredient Details
   - Add/Edit Ingredient (with moderation)
4. **Reviews & Tasting Notes**
   - Add Review/Note
   - Edit/Delete Review
   - Like/Comment on Review
   - Get Reviews for Drink/Ingredient
5. **Collections & Wishlists**
   - Create/Edit/Delete Collection
   - Add/Remove Drink to/from Collection
   - Set Collection Privacy
   - Get User Collections
6. **Discovery & Feed**
   - Trending Drinks
   - Top Rated
   - Personalized Recommendations
   - Activity Feed
   - Random Drink

### Environment Variables

- Development
- Staging
- Production

### Documentation Standards

- Each endpoint: description, example request/response, error codes
- Pre-request scripts for authentication
- Test scripts for validation

## 🐳 Docker File Structure

```
project/
├── docker-compose.yml
├── docker-compose.prod.yml
├── Dockerfile
├── .dockerignore
├── .github/
│   └── workflows/
│       ├── ci.yml
│       └── deploy.yml
├── docker/
│   ├── postgres/
│   └── redis/
├── postman/
│   ├── Spirited_API.postman_collection.json
│   └── Spirited_Environment.postman_environment.json
└── scripts/
    ├── docker-build.sh
    ├── docker-deploy.sh
    └── setup-env.sh
```

---

**Remember**: This is a real-world, portfolio-worthy project for hobbyist bartenders and drink lovers. Focus on clean code, great documentation, and a fun, social user experience!

Good luck! 🥂
