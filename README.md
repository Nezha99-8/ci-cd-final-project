# Counter REST API Service

A lightweight Flask-based REST API service for managing counters. This service provides a simple counter API where users can create, read, update, and delete named counters.

## Features

- **Create Counter**: Create new named counters with initial value of 0
- **Read Counter**: Retrieve the current value of a counter
- **Update Counter**: Increment a counter by 1
- **Delete Counter**: Remove a counter
- **List Counters**: View all existing counters
- **Health Check**: Endpoint to verify service health

## Technology Stack

- **Language**: Python 3.9
- **Framework**: Flask 2.1.2
- **WSGI Server**: Gunicorn 20.1.0
- **Containerization**: Docker
- **CI/CD**: GitHub Actions, Tekton
- **Testing**: nose, coverage

## Prerequisites

- Python 3.9 or higher
- Docker (for containerized deployment)
- Git

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd ci-cd-final-project
```

2. Create a virtual environment (optional but recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

## Running the Service

### Local Development

Using Honcho (recommended for development):
```bash
honcho start
```

Using Gunicorn directly:
```bash
gunicorn "service:app" --bind 0.0.0.0:8000
```

The service will be available at: `http://localhost:8000`

### Using Docker

Build the Docker image:
```bash
docker build -t counter-service .
```

Run the container:
```bash
docker run -p 8000:8000 counter-service
```

### Using Heroku

The service is configured for Heroku deployment via the `Procfile`:
```bash
heroku create
git push heroku main
```

## Testing

Run the test suite:
```bash
nosetests -v --with-spec --spec-color
```

Run with coverage:
```bash
coverage run -m nose
coverage report -m
```

Run specific linters:
```bash
flake8 .
pylint service/
black --check service/
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Index page with service information |
| GET | `/health` | Health check endpoint |
| GET | `/counters` | List all counters |
| POST | `/counters/<name>` | Create a new counter |
| GET | `/counters/<name>` | Read a counter |
| PUT | `/counters/<name>` | Increment a counter |
| DELETE | `/counters/<name>` | Delete a counter |

### Example Usage

**Create a counter:**
```bash
curl -X POST http://localhost:8000/counters/mycounter
```

**Read a counter:**
```bash
curl http://localhost:counters/mycounter
```

**Increment a counter:**
```bash
curl -X PUT http://localhost:8000/counters/mycounter
```

**List all counters:**
```bash
curl http://localhost:8000/counters
```

**Delete a counter:**
```bash
curl -X DELETE http://localhost:8000/counters/mycounter
```

## Project Structure

```
ci-cd-final-project/
├── bin/                    # Setup and utility scripts
├── service/                # Main service code
│   ├── __init__.py        # Flask app initialization
│   ├── routes.py          # API route handlers
│   └── common/            # Common utilities
│       ├── error_handlers.py
│       ├── log_handlers.py
│       └── status.py
├── tests/                 # Test suite
│   └── test_routes.py
├── .github/               # GitHub Actions workflows
├── .tekton/               # Tekton CI/CD tasks
├── Dockerfile             # Docker image definition
├── Procfile               # Heroku deployment config
├── pvc.yaml               # Kubernetes PVC
├── flake8.yaml            # Tekton linting task
├── requirements.txt      # Python dependencies
├── setup.cfg              # Project configuration
└── LICENSE                # Apache 2.0 License
```

## CI/CD Pipeline

### GitHub Actions
The project includes GitHub Actions workflows for continuous integration.

### Tekton
Tekton tasks are defined in the project for Kubernetes-based CI/CD:
- `flake8.yaml`: Linting task

### Docker
The `Dockerfile` builds a production-ready container image.


