# CloudCart

A cloud computing demonstration project built around a **microservices architecture** using Python and FastAPI.

CloudCart explores the fundamentals of distributed application development, including independent services, database integration, inter-service communication, containerization, and automated CI/CD pipelines.

The project consists of two independently structured services: a User Service and an Orders Service.

## Architecture

The application follows a microservices-oriented architecture, separating user management and order management into independent services.

```text
                  Cloud Demo
                      |
          +-----------+-----------+
          |                       |
     User Service           Orders Service
          |                       |
     Database                Database
          |                       |
          +----------+------------+
                     |
              Message Broker
                 RabbitMQ
```

### Services

**User Service**

Responsible for user-related operations and authentication.

**Orders Service**

Responsible for order-related operations and order management.

Each service maintains its own application structure and can be developed, tested, and containerized independently.

## Technology Stack

| Component | Technology |
|---|---|
| Language | Python 3.11 |
| API Framework | FastAPI |
| ORM | SQLAlchemy |
| Database Migrations | Alembic |
| Validation | Pydantic |
| Databases | SQLite / PostgreSQL |
| Message Broker | RabbitMQ |
| Authentication | JWT |
| Password Hashing | bcrypt |
| ASGI Server | Uvicorn |
| Containerization | Docker |
| CI/CD | GitHub Actions |
| Testing | Pytest |
| Code Quality | Ruff, Black, Isort |

## Project Structure

```text
Cloud_Demo/
│
├── .github/
│   └── workflows/          # CI/CD workflows
│
├── orders-service/
│   ├── app/                # Orders application
│   ├── tests/              # Orders tests
│   └── ...
│
├── user-service/
│   ├── app/                # User application
│   ├── tests/              # User tests
│   └── ...
│
├── CI-CD-GUIDE.md          # CI/CD documentation
├── conftest.py             # Pytest configuration
├── pyproject.toml          # Development tool configuration
├── requirements.txt        # Python dependencies
└── README.md
```

## Getting Started

### Prerequisites

- Python 3.11+
- pip
- Git
- Docker (for containerized deployment)
- PostgreSQL and RabbitMQ (for integration testing and configured deployments)

### Installation

Clone the repository:

```bash
git clone https://github.com/hoarah-loux/Cloud_Demo.git
cd Cloud_Demo
```

Create and activate a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

### Running the Services

The User Service and Orders Service are separate applications.

Their application entry points and configuration determine the commands used to launch each service. Configure their respective environment variables and database connections before starting them.

## Testing

The project uses Pytest for automated testing.

Run the complete test suite:

```bash
pytest
```

Run individual service tests:

```bash
pytest orders-service/tests -v
pytest user-service/tests -v
```

Run tests with coverage:

```bash
pytest --cov=orders-service/app
pytest --cov=user-service/app
```

Integration tests are also provided for testing interactions with PostgreSQL and RabbitMQ.

## CI/CD

The project uses GitHub Actions to automate development workflows.

The pipeline includes:

- **Automated Testing:** Executes the test suites on pushes and pull requests.
- **Code Quality:** Runs Ruff, Black, and Isort checks.
- **Docker Builds:** Builds service images on the main branch.
- **Container Registry:** Publishes Docker images to GitHub Container Registry.
- **Integration Testing:** Tests cross-service communication using PostgreSQL and RabbitMQ.
- **Security Checks:** Uses Bandit and Safety.

Kubernetes deployment configuration is included in the CI/CD documentation but is currently disabled.

For additional configuration details, see [CI-CD-GUIDE.md](CI-CD-GUIDE.md).

## Project Scope

Cloud Demo is intended to demonstrate practical cloud computing concepts through a small distributed application.

The primary focus is on:

- Microservices architecture.
- Separation of application responsibilities.
- Database integration and migrations.
- Asynchronous inter-service communication.
- Authentication and security fundamentals.
- Containerization.
- Automated testing and deployment pipelines.

The project focuses on backend infrastructure and service architecture. It does not currently provide a user-facing frontend.

---

**License:** Not specified.
