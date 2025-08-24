# 🏐 Volleyball Analytics Backend

A high-performance, maintainable FastAPI backend for volleyball analytics, designed with modern Python practices and clean architecture principles.

## ✨ Features

- **🚀 FastAPI Framework**: High-performance async API with automatic OpenAPI documentation
- **🗄️ PostgreSQL Support**: Robust database with connection pooling and migrations
- **🔒 Type Safety**: Full type hints and Pydantic validation
- **📊 Comprehensive API**: Complete CRUD operations for all volleyball entities
- **🛡️ Error Handling**: Standardized error responses and logging
- **🧪 Testing Ready**: Built-in test configuration and utilities
- **📈 Monitoring**: Health checks, metrics, and performance monitoring
- **🔧 Flexible Configuration**: Environment-aware settings with fallbacks

## 🏗️ Architecture

```
volleyball_backend/
├── 📁 core/                    # Core configuration and utilities
│   ├── config.py              # Settings and environment management
│   └── __init__.py
├── 📁 db/                      # Database layer
│   ├── engine.py              # Connection management and pooling
│   └── __init__.py
├── 📁 api/                     # API layer
│   ├── api.py                 # Main router configuration
│   ├── endpoints/             # Individual endpoint modules
│   └── __init__.py
├── 📁 models/                  # SQLAlchemy ORM models
├── 📁 schemas/                 # Pydantic data validation schemas
├── 📁 crud/                    # Database CRUD operations
├── 📁 enums/                   # Enumeration definitions
├── 📁 tests/                   # Test suite
├── app.py                      # Main FastAPI application
├── api_interface.py            # High-level API interface
├── pyproject.toml              # Project configuration
└── README.md                   # This file
```

## 🚀 Quick Start

### Prerequisites

- Python 3.9+
- PostgreSQL (or SQLite for development)
- pip or uv package manager

### Installation

#### Option 1: Install as Package (Recommended)
```bash
# Clone the repository
git clone git@github.com:masouduut94/volleyball-backend.git
cd volleyball-backend

# Install in development mode
pip install -e .

# Or using uv
uv sync
```

#### Option 2: Manual Installation
```bash
# Install dependencies
pip install fastapi uvicorn sqlalchemy psycopg2-binary pydantic loguru

# Or install with extras
pip install -e ".[dev,test]"
```

### Configuration

Create a `.env` file in the project root:

```env
# Environment
MODE=development
DEBUG=true

# Database
DEV_USERNAME=postgres
DEV_PASSWORD=your_password
DEV_HOST=localhost
DEV_DB=volleyball_development
DEV_PORT=5432
DEV_DRIVER=postgresql

# Application
PROJECT_NAME=volleyball_analytics
API_PREFIX=/api
API_VERSION=v1

# Security
SECRET_KEY=your-secret-key-here
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

### Running the Application

#### Development Mode
```bash
# Start with auto-reload
uvicorn volleyball_backend.app:app --reload --port 8000

# Or use the built-in runner
python -m volleyball_backend.app
```

#### Production Mode
```bash
# Set production environment
export MODE=production

# Start production server
uvicorn volleyball_backend.app:app --host 0.0.0.0 --port 8000
```

### API Documentation

Once running, access the interactive API documentation:

- **Swagger UI**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc
- **OpenAPI JSON**: http://localhost:8000/openapi.json

## 📚 API Endpoints

### Core Endpoints
- `GET /` - Service information
- `GET /health` - Health check
- `GET /api/check` - API status

### Entity Endpoints
- `GET/POST /api/v1/cameras` - Camera management
- `GET/POST /api/v1/matches` - Match management
- `GET/POST /api/v1/nations` - Nation management
- `GET/POST /api/v1/players` - Player management
- `GET/POST /api/v1/rallies` - Rally management
- `GET/POST /api/v1/series` - Series management
- `GET/POST /api/v1/teams` - Team management
- `GET/POST /api/v1/videos` - Video management

## 🗄️ Database

### Connection Management
- **Connection Pooling**: Configurable pool size and overflow
- **Health Checks**: Automatic connection validation
- **Migration Support**: Alembic integration ready

### Models
- **Base Model**: Common fields and methods
- **Relationships**: Proper foreign key constraints
- **Validation**: Pydantic schema integration

## 🧪 Testing

### Running Tests
```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=volleyball_backend

# Run specific test categories
pytest -m "unit"
pytest -m "integration"
pytest -m "api"
```

### Test Configuration
- **Unit Tests**: Fast, isolated component testing
- **Integration Tests**: Database and API integration
- **API Tests**: End-to-end endpoint testing
- **Database Tests**: Transaction rollback testing

## 🔧 Development

### Code Quality
```bash
# Format code
black volleyball_backend/

# Sort imports
isort volleyball_backend/

# Type checking
mypy volleyball_backend/

# Linting
flake8 volleyball_backend/
```

### Pre-commit Hooks
```bash
# Install pre-commit
pip install pre-commit

# Install hooks
pre-commit install

# Run on all files
pre-commit run --all-files
```

## 📦 Package Management

### Dependencies
- **Core**: FastAPI, SQLAlchemy, Pydantic
- **Database**: PostgreSQL driver, connection pooling
- **Development**: Testing, linting, formatting tools
- **Optional**: Authentication, caching, monitoring

### Installation Options
```bash
# Core package only
pip install volleyball-backend

# With development tools
pip install volleyball-backend[dev]

# With testing tools
pip install volleyball-backend[test]

# With all extras
pip install volleyball-backend[dev,test]
```

## 🌐 Integration

### As a Submodule
This backend is designed to work seamlessly as a Git submodule in the main volleyball analytics project:

```bash
# In the main project
git submodule add git@github.com:masouduut94/volleyball-backend.git src/backend

# Update submodules
git submodule update --init --recursive
```

### Import Usage
```python
# Import the main app
from volleyball_backend import app

# Import specific components
from volleyball_backend.core.config import settings
from volleyball_backend.db.engine import get_db
from volleyball_backend.api_interface import APIInterface

# Use the API interface
api = APIInterface()
response = api.get_teams()
```

## 🚀 Deployment

### Docker
```dockerfile
FROM python:3.11-slim

WORKDIR /app
COPY . .
RUN pip install -e .

EXPOSE 8000
CMD ["uvicorn", "volleyball_backend.app:app", "--host", "0.0.0.0", "--port", "8000"]
```

### Environment Variables
```bash
# Production settings
export MODE=production
export DEBUG=false
export DEV_HOST=your-db-host
export DEV_DB=your-db-name
export DEV_USERNAME=your-db-user
export DEV_PASSWORD=your-db-password
```

## 📊 Monitoring

### Health Checks
- **Database Connection**: Automatic validation
- **API Endpoints**: Response time monitoring
- **System Resources**: Memory and CPU usage

### Logging
- **Structured Logging**: JSON format with context
- **Log Levels**: Configurable verbosity
- **Performance Metrics**: Request timing and database queries

## 🤝 Contributing

### Development Setup
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Ensure all tests pass
6. Submit a pull request

### Code Standards
- Follow PEP 8 style guidelines
- Use type hints for all functions
- Write comprehensive docstrings
- Maintain test coverage above 90%

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Related Projects

- [Volleyball Analytics ML Manager](https://github.com/masouduut94/volleyball-ml-models)
- [Main Volleyball Analytics Repository](https://github.com/masouduut94/volleyball_analytics)

## 📞 Support

For questions, issues, or contributions:

- **Issues**: [GitHub Issues](https://github.com/masouduut94/volleyball-backend/issues)
- **Discussions**: [GitHub Discussions](https://github.com/masouduut94/volleyball-backend/discussions)
- **Documentation**: [API Docs](http://localhost:8000/docs) (when running)

---

**Built with ❤️ for the volleyball community**
