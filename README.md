# 5e-hammergen

5th ed. Warhammer Fantasy Roleplay character generator and campaign toolkit.

## Overview

**5e-hammergen** is the next iteration of [wfrp-hammergen](https://github.com/jmilosze/wfrp-hammergen), rebuilt with a modern stack for fast, intuitive, and rich character creation and rule management.

## Architecture

The Go backend uses a simplified two-layer architecture:
1. **Web Layer:** HTTP routing via Chi, OpenAPI request validation via `kin-openapi`, contract enforcement via `oapi-codegen`, authentication (JWT/OAuth2), reCAPTCHA verification, and response serialization.
2. **Service Layer:** Business domain logic with embedded MongoDB data access, eliminating unnecessary database abstraction interfaces.

## Tech Stack & Infrastructure

- **API Contract:** OpenAPI 3.0+ YAML specification (single source of truth)
- **Backend:** Go (Golang)
  - Code Generator: [`oapi-codegen`](https://github.com/oapi-codegen/oapi-codegen) (generates Go types and Chi server routing)
  - Request Validation: [`kin-openapi` Chi middleware](https://github.com/oapi-codegen/oapi-codegen/tree/main/pkg/middleware) (automatic schema & payload validation)
  - Router: [`go-chi/chi/v5`](https://github.com/go-chi/chi)
  - CORS: [`rs/cors`](https://github.com/rs/cors)
  - JWT Auth: [`golang-jwt/jwt/v5`](https://github.com/golang-jwt/jwt)
  - OAuth2 (Google & GitHub): [`golang.org/x/oauth2`](https://pkg.go.dev/golang.org/x/oauth2)
  - Transactional Email: [`resend-go/v2`](https://github.com/resend/resend-go)
  - Anti-Abuse: Google reCAPTCHA v3
  - Database Driver: [`go.mongodb.org/mongo-driver/v2`](https://go.mongodb.org/mongo-driver/v2)
  - Deployment: GCP Cloud Run as `hammergen`
- **Frontend:** Vue 3 + TypeScript
  - Bundler: [Vite](https://vitejs.dev/)
  - Styling: [Tailwind CSS v4](https://tailwindcss.com/)
  - UI Components (Optional): [`shadcn-vue`](https://www.shadcn-vue.com/) (accessible Tailwind primitives)
  - Routing: [`vue-router`](https://router.vuejs.org/)
  - Icons: [`@iconify/vue`](https://iconify.design/)
  - Code Generator: [`openapi-typescript`](https://openapi-ts.dev/) (generates TypeScript interfaces and typed fetch clients)
  - Captcha: [`vue-recaptcha-v3`](https://github.com/AStarStartup/vue-recaptcha-v3)
  - Testing: [Vitest](https://vitest.dev/)
  - Deployment: Cloudflare Pages
- **Database:** MongoDB (hosted in a GCP cluster for low-latency access)

## Project Structure

```
5e-hammergen/
├── Makefile                 # Build, generation, and dev automation
├── docker-compose.yaml      # Local MongoDB container
├── openapi/
│   ├── openapi.yaml         # Single source of truth API specification
│   └── oapi-codegen.yaml    # Go generator configuration
├── backend/
│   ├── cmd/server/main.go
│   ├── internal/
│   │   ├── web/             # Chi router, oapi handlers, auth, middleware
│   │   └── service/         # Business logic with MongoDB operations
│   └── go.mod
└── frontend/
    ├── src/
    │   ├── api/             # Generated OpenAPI types & fetch client
    │   ├── components/
    │   ├── views/
    │   └── main.ts
    ├── package.json
    └── vite.config.ts
```

## Local Development

- **Start Database:** `docker compose up -d`
- **Generate API Code:** `make gen` (runs `oapi-codegen` and `openapi-typescript`)
- **Run Backend:** `make dev-backend`
- **Run Frontend:** `make dev-frontend`
- 