# Development Guide

This document provides guidelines for developers working on the Asset Management and NCRS System.

## Getting Started

### Prerequisites

- Docker and Docker Compose
- Node.js v18+
- Python 3.10+
- Git

### Development Environment Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/Zweiblum66/asset-management-ncrs.git
   cd asset-management-ncrs
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development environment:
   ```bash
   npm run start
   ```

4. Access the services:
   - Frontend: http://localhost:3000
   - API Documentation: http://localhost:8080/api-docs
   - MinIO Console: http://localhost:9001 (minioadmin/minioadmin)
   - RabbitMQ Management: http://localhost:15672 (guest/guest)

## Project Structure

The project follows a monorepo structure:

- **services/**: Backend microservices
- **frontend/**: React frontend application
- **shared/**: Shared libraries and utilities
- **infrastructure/**: Infrastructure as code
- **docs/**: Project documentation
- **tools/**: Development and operational tools

## Development Workflow

### Branching Strategy

We follow the GitFlow branching model:

- `main`: Production-ready code
- `develop`: Latest development changes
- `feature/*`: New features
- `bugfix/*`: Bug fixes
- `release/*`: Release preparation
- `hotfix/*`: Urgent production fixes

### Creating a New Feature

1. Create a new branch from `develop`:
   ```bash
   git checkout develop
   git pull
   git checkout -b feature/your-feature-name
   ```

2. Make your changes and commit them:
   ```bash
   git add .
   git commit -m "feat: your feature description"
   ```

3. Push your branch and create a pull request:
   ```bash
   git push -u origin feature/your-feature-name
   ```

### Commit Message Format

We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

Types:
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, semicolons, etc)
- `refactor`: Code changes that neither fix bugs nor add features
- `perf`: Performance improvements
- `test`: Adding or fixing tests
- `chore`: Changes to the build process or auxiliary tools

## Code Standards

### JavaScript/TypeScript

- Use ESLint and Prettier for code formatting
- Follow the Airbnb JavaScript Style Guide
- Use TypeScript for type safety
- Write unit tests for all new features

### Python

- Follow PEP 8 style guide
- Use type hints
- Use pytest for testing

## Testing

### Running Tests

```bash
# Run all tests
npm test

# Run tests for a specific workspace
npm test --workspace=services/api-gateway
```

### Test Coverage

We aim for a minimum of 80% test coverage for all new code.

## Building for Production

```bash
# Build all services
npm run build

# Build a specific service
npm run build --workspace=services/api-gateway
```

## CI/CD Pipeline

Our CI/CD pipeline consists of:

1. Linting and testing on all pull requests
2. Building and testing on merges to `develop`
3. Deployment to staging environment from `develop`
4. Deployment to production from `main`

## Documentation

- API documentation is generated from OpenAPI specifications
- Update documentation when making changes to APIs or architecture
- Document all new features and configuration options 