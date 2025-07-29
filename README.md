# Smartess

**An all-in-one smart home management platform for residential communities**

Smartess bridges the gap between tenants and property owners through intelligent home automation and centralized management. While tenants enjoy a fully integrated smart home experience in their units, property owners gain comprehensive oversight through real-time monitoring, automated communication tools, and data-driven insights.

**Live Demo:** https://smartess.vercel.app/

## Overview

Property management in modern residential communities requires sophisticated tools to handle smart home devices, tenant communications, and building operations effectively. Smartess addresses these challenges by providing a unified platform that collects data from smart appliances and IoT devices, processes it in real-time, and presents actionable insights through an intuitive web interface.

The platform serves dual purposes: empowering tenants with seamless smart home control while giving property owners the visibility and tools they need to manage their buildings efficiently. From automated maintenance request handling to real-time energy consumption monitoring, Smartess transforms how residential communities operate.

## Team

| Name                   | GitHub                                            | Email                         |
| ---------------------- | ------------------------------------------------- | ----------------------------- |
| **Lauren Rigante**     | [laurenrigante](https://github.com/laurenrigante) | lrigante@hotmail.com          |
| Leo Brodeur            | [leobrod44](https://github.com/leobrod44)         | leobrod44@gmail.com           |
| Layana Muhdi Al Tounsi | [layanat](https://github.com/layanat)             | tounsilayana@gmail.com        |
| Charles Eimer          | [eimcharles](https://github.com/eimcharles)       | c.eimer@me.com                |
| Antoine Cantin         | [ChiefsBestPal](https://github.com/ChiefsBestPal) | antoine.cantin@icloud.com     |
| Tuan Anh Pham          | [TuanAnh-P](https://github.com/TuanAnh-P)         | 1tuananhp@gmail.com           |
| Matthew Flaherty       | [mattflahertyy](https://github.com/mattflahertyy) | matthewflaherty77@hotmail.com |
| Renaud Senécal         | [SenecalRenaud](https://github.com/SenecalRenaud) | senecalrenaud@gmail.com       |
| Ryan Li                | [Ryan2Li](https://github.com/Ryan2Li)             | ryanlijune@gmail.com          |
| Abdullah Amir          | [AA789-ai](https://github.com/AA789-ai)           | sonubhaii883@gmail.com        |

## Technology Stack

### Backend Services

- **Go**: High-performance microservices architecture
- **RabbitMQ**: Message queuing and event streaming
- **MongoDB**: Primary database for application data
- **Supabase**: Authentication and real-time features
- **WebRTC**: Real-time video communication

### Frontend

- **Next.js 14**: React-based web framework
- **TypeScript**: Type-safe development
- **Tailwind CSS**: Utility-first styling
- **Material-UI**: Component library
- **Recharts**: Data visualization

### Infrastructure & Monitoring

- **Docker**: Containerization and deployment
- **Grafana**: Metrics visualization and dashboards
- **Loki**: Centralized logging
- **Prometheus**: Metrics collection and monitoring
- **Promtail**: Log aggregation

### Integration

- **Home Assistant**: Smart home device orchestration
- **RTSP**: Video streaming protocol
- **STOMP**: Real-time messaging protocol

## Architecture

Smartess follows a distributed microservices architecture designed for scalability and reliability:

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Smart Hubs    │────│   Go Services    │────│  Web Platform   │
│ (Home Assistant)│    │  (Microservices) │    │   (Next.js)     │
└─────────────────┘    └──────────────────┘    └─────────────────┘
        │                        │                        │
        │                ┌───────▼────────┐               │
        │                │   RabbitMQ     │               │
        │                │ (Message Bus)  │               │
        │                └────────────────┘               │
        │                                                 │
        └─────────────────────────────────────────────────┘
                    Event Flow & Real-time Updates
```

**Hub Layer**: Home Assistant instances collect data from smart devices and sensors within individual units, publishing events to the message bus.

**Service Layer**: Go-based microservices handle video streaming, event processing, data persistence, and integration with external systems.

**Web Layer**: Next.js application provides the user interface for both tenants and property managers, with role-based access control and real-time updates.

**Message Bus**: RabbitMQ ensures reliable communication between all system components, enabling real-time event processing and system resilience.

## Quick Start

### Prerequisites

- Docker and Docker Compose
- Go 1.23 or later
- Node.js 18 or later
- Git

### Development Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/leobrod44/Smartess.git
   cd Smartess
   ```

2. **Start the complete system**

   ```bash
   docker-compose up -d
   ```

3. **For development work on individual components:**

   **Hub Development:**

   ```bash
   cd go
   # See go/README.md for detailed setup instructions
   ```

   **Web Development:**

   ```bash
   cd smartessweb
   # See smartessweb/README.md for detailed setup instructions
   ```

### Accessing the Application

- **Web Interface**: http://localhost:3000
- **API Documentation**: http://localhost:8080/docs
- **Grafana Dashboard**: http://localhost:4000
- **RabbitMQ Management**: http://localhost:15672

## Key Features

- **Real-time Monitoring**: Live video streams and sensor data from all connected units
- **Event Management**: Automated alert processing and notification system
- **User Management**: Role-based access control for tenants, managers, and administrators
- **Maintenance Requests**: Digital ticketing system for tenant-to-owner communication
- **Energy Analytics**: Consumption tracking and optimization recommendations
- **Communication Hub**: Automated emails and community announcements
- **Multi-tenant Architecture**: Secure isolation between different properties and units

## Project Structure

```
├── go/                          # Backend services and hub integration
│   ├── cmd/                     # Executable applications
│   ├── common/                  # Shared utilities and configurations
│   ├── hub/                     # Home Assistant integration
│   ├── server/                  # Main API server
│   └── tests/                   # Integration and unit tests
├── smartessweb/                 # Web application
│   ├── backend/                 # Node.js API server
│   ├── frontend/                # Next.js React application
│   └── tests/                   # Frontend and backend tests
├── observability/               # Monitoring and logging stack
│   ├── grafana/                 # Dashboard configurations
│   ├── loki/                    # Log aggregation setup
│   └── prometheus/              # Metrics collection config
└── admin/                       # Project documentation and contracts
```

## Key Components

### Critical Files

| Component                                                                                                                            | Purpose                                            |
| ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------- |
| [`go/hub/rtsp/rtsp.go`](go/hub/rtsp/rtsp.go)                                                                                         | Video stream processing and RabbitMQ publishing    |
| [`go/hub/events/events.go`](go/hub/events/events.go)                                                                                 | Home Assistant event handling and alert processing |
| [`smartessweb/frontend/src/app/dashboard/page.tsx`](smartessweb/frontend/src/app/dashboard/page.tsx)                                 | Main dashboard interface                           |
| [`smartessweb/backend/controllers/manageAccountsController.js`](smartessweb/backend/controllers/manageAccountsController.js)         | User account management logic                      |
| [`smartessweb/frontend/src/app/dashboard/manage-accounts/page.tsx`](smartessweb/frontend/src/app/dashboard/manage-accounts/page.tsx) | Role-based user management UI                      |

### Test Coverage

| Test File                                                                                                                                          | Purpose                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| [`go/tests/rtsp_test.go`](go/tests/rtsp_test.go)                                                                                                   | RTSP stream integration testing     |
| [`smartessweb/backend/tests/controllers/manageAccountsController.test.js`](smartessweb/backend/tests/controllers/manageAccountsController.test.js) | Account management API testing      |
| [`smartessweb/backend/tests/controllers/projectController.test.js`](smartessweb/backend/tests/controllers/projectController.test.js)               | Project data retrieval testing      |
| [`smartessweb/backend/tests/controllers/ticketsController.test.js`](smartessweb/backend/tests/controllers/ticketsController.test.js)               | Maintenance ticket system testing   |
| [`smartessweb/frontend/__tests__/ProjectComponent.test.tsx`](smartessweb/frontend/__tests__/ProjectComponent.test.tsx)                             | Frontend component behavior testing |

### Development Guidelines

- Follow the established patterns in each technology stack
- Write comprehensive tests for new features
- Document any new APIs or significant changes
- Use conventional commit messages
- Ensure Docker builds pass before submitting

### Code Quality

Our CI pipeline automatically runs:

- ESLint for code quality checks
- Jest for comprehensive testing
- Docker builds for deployment validation
- Security scans for dependency vulnerabilities

## Release History

### Release 3 (Current)

- Enhanced user management with role-based permissions
- Improved real-time video streaming performance
- Advanced analytics dashboard with energy consumption tracking
- [Demo Video](https://drive.google.com/file/d/1w1BCWQPlqrisWkyoj2oj-TvpI7K_VQ4S/view?usp=sharing)
- [Presentation Slides](https://github.com/user-attachments/files/19696745/_Smartess.Release.3.Presentation.pdf)

### Release 2

- Integrated Home Assistant event processing
- Multi-tenant architecture implementation
- Automated notification system
- [Demo Video](https://drive.google.com/file/d/1MvIh3tUW6fsqQBHBUWBLqvQHEsESYOVF/view?usp=sharing)
- [Presentation Slides](https://github.com/user-attachments/files/19556576/Smartess.Release.2.Presentation.pdf)

### Release 1

- Core platform architecture
- Basic dashboard functionality
- Initial hub integration
- [Demo Video](https://drive.google.com/file/d/1VhbKIfahZcb6RqXoC6UfZoBpeX1w_sCs/view?usp=sharing)

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Diversity and Inclusion

Smartess is committed to building technology that serves diverse communities effectively. We believe that inclusive design leads to better solutions, and we actively work to ensure our platform is accessible to users regardless of their technical background, cultural context, or physical abilities. Our development practices prioritize user-centered design and accessibility standards to create truly inclusive smart home experiences.
