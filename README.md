# 5e-hammergen

5th ed. Warhammer Fantasy Roleplay character generator and campaign toolkit.

## Overview

**5e-hammergen** is the next iteration of [wfrp-hammergen](https://github.com/jmilosze/wfrp-hammergen), rebuilt with a modern stack for fast, intuitive, and rich character creation and rule management.

## Tech Stack & Infrastructure

- **API Contract:** OpenAPI 3.0+ YAML specification (single source of truth)
- **Backend:** Go (Golang)
  - Code Generator: [`oapi-codegen`](https://github.com/oapi-codegen/oapi-codegen) (generates Go types and Chi server routing)
  - Router: [`go-chi/chi/v5`](https://github.com/go-chi/chi)
  - CORS: [`rs/cors`](https://github.com/rs/cors)
  - JWT Auth: [`golang-jwt/jwt/v5`](https://github.com/golang-jwt/jwt)
  - OAuth2 (Google & GitHub): [`golang.org/x/oauth2`](https://pkg.go.dev/golang.org/x/oauth2)
  - Transactional Email: [`resend-go/v2`](https://github.com/resend/resend-go)
  - Anti-Abuse: Google reCAPTCHA v3
  - Database Driver: [`go.mongodb.org/mongo-driver/v2`](https://go.mongodb.org/mongo-driver/v2)
  - Deployment: GCP Cloud Run as `hammergen`
- **Frontend:** Vue 3 + TypeScript
  - Code Generator: [`openapi-typescript`](https://openapi-ts.dev/) (generates TypeScript interfaces and typed fetch clients)
  - Captcha: [`vue-recaptcha-v3`](https://github.com/AStarStartup/vue-recaptcha-v3)
  - Deployment: Cloudflare Pages
- **Database:** MongoDB (hosted in a GCP cluster for low-latency access)

## Development

*Project structure and setup instructions will be updated as modules are implemented.*
