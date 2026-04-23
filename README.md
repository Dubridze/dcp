# PropTech Equipment Portal

Portal for collecting equipment procurement requests.

## Stack

| Layer | Technology |
|---|---|
| Frontend | React 18 + Vite, React Query, React Hook Form |
| Backend | Python 3.12, FastAPI, SQLAlchemy 2 (async) |
| Auth | Keycloak 24 (OIDC / JWT RS256) |
| Database | PostgreSQL 16 |
| Container | Docker + Docker Compose |

## Quick Start

```bash
docker compose up --build -d
```

- App: http://localhost
- Keycloak Admin: http://localhost:8080 (admin / admin)
- API Swagger: http://localhost:8000/api/docs

## Keycloak Setup

1. Open http://localhost:8080 → log in with admin / admin
2. Create realm: `proptech`
3. Create clients:
   - `portal-frontend` — Public, Redirect URI: `http://localhost/*`, Web Origins: `http://localhost`
   - `portal-backend` — Bearer-only
4. Create realm roles: `admin`, `approver`, `user`
5. Create test users and assign roles

## Role Model

| Role | Permissions |
|---|---|
| user | Create and view own requests |
| approver | + View all requests, approve/reject |
| admin | + Manage catalog and portal settings |

## Customization

Edit CSS tokens in `frontend/src/theme.css`.
Portal name, logo color, and accent color are also configurable in the Admin → Settings UI page.
