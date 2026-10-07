# AlgoTrading Platform

A production-grade algorithmic trading platform built with FastAPI, React, and the Dhan broker API.

## Architecture

```
frontend/    → React + Vite + TypeScript + Material UI
backend/     → FastAPI + SQLAlchemy + Celery
```

### Trading Engine Flow

```
Strategy → Signal Generator → Risk Manager → Order Manager → Broker Interface → Dhan API
```

The broker layer is fully abstracted — swap Dhan for Zerodha, Angel One, or any other broker by implementing the `Broker` interface.

## Tech Stack

| Layer          | Technology                                      |
|----------------|------------------------------------------------|
| Frontend       | React, Vite, TypeScript, Material UI, Recharts |
| Backend        | FastAPI, SQLAlchemy, Pydantic, Alembic         |
| Database       | PostgreSQL                                      |
| Cache/Queue    | Redis                                           |
| Task Queue     | Celery                                          |
| Broker         | Dhan (abstracted)                               |
| Auth           | JWT (access + refresh tokens)                   |
| Infrastructure | Docker, Docker Compose                          |

## Getting Started

```bash
# 1. Copy environment file
cp .env.example .env

# 2. Fill in your secrets in .env

# 3. Start all services
docker-compose up --build
```

## Project Structure

```
backend/app/
├── api/routes/       # REST endpoints
├── core/             # Config, security, database
├── models/           # SQLAlchemy models
├── schemas/          # Pydantic schemas
├── services/         # Business logic
├── repositories/     # Data access
├── brokers/          # Broker abstraction
├── trading/          # Trading engine
├── strategies/       # Strategy implementations
├── workers/          # Celery tasks
├── websocket/        # WebSocket handlers
└── utils/            # Helpers

frontend/src/
├── components/       # Reusable UI
├── pages/            # Route-level pages
├── layouts/          # Page layouts
├── hooks/            # Custom hooks
├── services/         # API + WebSocket clients
├── store/            # State management
├── types/            # TypeScript types
├── utils/            # Helpers
└── routes/           # Route config
```

## Development Phases

This project is built incrementally across 26 phases. See the development plan for details.
