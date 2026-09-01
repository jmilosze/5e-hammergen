# 5e-hammergen

5th ed. Warhammer Fantasy Roleplay character generator and campaign toolkit.

## Overview

**5e-hammergen** is the next iteration of [wfrp-hammergen](https://github.com/jmilosze/wfrp-hammergen), rebuilt with a modern stack for fast, intuitive, and rich character creation and rule management.

## Architecture

The Go backend uses a simplified two-layer architecture:
1. **Web Layer:** HTTP routing via Chi, OpenAPI request validation via `kin-openapi`, contract enforcement via `oapi-codegen`, authentication (JWT/OAuth2), reCAPTCHA verification, and response serialization.
2. **Service Layer:** Business domain logic with embedded MongoDB data access, eliminating unnecessary database abstraction interfaces.

## Tech Stack

- **API Contract:** OpenAPI 3.0+ YAML specification (single source of truth)
- **Backend:** Go (Golang)
  - Code Generator: [`oapi-codegen`](https://github.com/oapi-codegen/oapi-codegen) (generates Go types and Chi server routing)
  - Request Validation: [`kin-openapi` Chi middleware](https://github.com/oapi-codegen/oapi-codegen/tree/main/pkg/middleware)
  - Router: [`go-chi/chi/v5`](https://github.com/go-chi/chi)
  - CORS: [`rs/cors`](https://github.com/rs/cors)
  - JWT Auth: [`golang-jwt/jwt/v5`](https://github.com/golang-jwt/jwt)
  - OAuth2 (Google & GitHub): [`golang.org/x/oauth2`](https://pkg.go.dev/golang.org/x/oauth2)
  - Transactional Email: [`resend-go/v2`](https://github.com/resend/resend-go)
  - Anti-Abuse: Google reCAPTCHA v3
  - Database Driver: [`go.mongodb.org/mongo-driver/v2`](https://go.mongodb.org/mongo-driver/v2)
- **Frontend:** Vue 3 + TypeScript
  - Bundler: [Vite](https://vitejs.dev/)
  - Styling: [Tailwind CSS v4](https://tailwindcss.com/)
  - UI Components (Optional): [`shadcn-vue`](https://www.shadcn-vue.com/)
  - Routing: [`vue-router`](https://router.vuejs.org/)
  - Icons: [`@iconify/vue`](https://iconify.design/)
  - Code Generator: [`openapi-typescript`](https://openapi-ts.dev/)
  - Captcha: [`vue-recaptcha-v3`](https://github.com/AStarStartup/vue-recaptcha-v3)
  - Testing: [Vitest](https://vitest.dev/)

## Infrastructure & Deployment

- **Database:** MongoDB (hosted in a GCP cluster for low-latency access)
- **Backend Hosting:** GCP Cloud Run
- **Frontend Hosting:** Cloudflare Pages
- **CI/CD:** GitHub Actions (automated linting, tests, and deployments)
