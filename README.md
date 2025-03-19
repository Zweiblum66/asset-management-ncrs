# Asset Management and NCRS System

Modern, compliance-ready asset management and News Content Repository System (NCRS) for video news production. This system provides a comprehensive platform for managing media assets with integrated workflows for journalists, video editors, editorial teams, and social media departments.

## Project Overview

This system is designed as a productizable platform deployable in various environments (on-premises, cloud, or hybrid) with integration capabilities for broadcast systems via MOS protocol and social media platforms. It follows an API-first approach with a responsive, cross-platform user interface that supports modern design principles including dark mode.

### Key Features

- Centralized repository for all media assets (video, audio, images, text)
- Integrated workflows for journalists, video editors, editorial teams, and social media departments
- Integration with playout systems via MOS protocol
- Direct export/API capabilities for social media platforms
- Compliance with industry standards (SOC2/ISO certifications)
- Modern, responsive user interface accessible across multiple device types

## Getting Started

### Prerequisites

- Docker and Docker Compose
- Node.js v18+
- Python 3.10+
- Git

### Setup Instructions

1. Clone the repository
2. Install Docker and Docker Compose
3. Run `docker-compose up -d` to start the development environment
4. Access the frontend at http://localhost:3000
5. Access API documentation at http://localhost:8080/api-docs

## Architecture

The system utilizes a microservices architecture with the following components:

- API Gateway
- Authentication Service
- Asset Management Service
- Metadata Service
- Search Service
- Transcoding Service
- Workflow Service
- Distribution Service
- MOS Connector
- Social Media Connector
- Analytics Service

## Technology Stack

- **Backend**: Node.js/TypeScript, Python
- **Frontend**: React, Tailwind CSS
- **Databases**: PostgreSQL, MongoDB, OpenSearch, Redis
- **Messaging**: Apache Kafka, RabbitMQ
- **Infrastructure**: Docker, Kubernetes

## Development

Please refer to the [development documentation](docs/development/README.md) for guidelines on contributing to this project.

## License

This project is proprietary software.