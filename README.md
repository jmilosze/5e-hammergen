# 5e-hammergen

5th ed. Warhammer Fantasy Roleplay character generator and campaign toolkit.

## Overview

**5e-hammergen** is the next iteration of [wfrp-hammergen](https://github.com/jmilosze/wfrp-hammergen), rebuilt with a modern stack for fast, intuitive, and rich character creation and rule management.

## Tech Stack & Infrastructure

- **Backend:** Go (Golang)
  - Router: [`go-chi/chi/v5`](https://github.com/go-chi/chi)
  - CORS: [`rs/cors`](https://github.com/rs/cors)
  - JWT Auth: [`golang-jwt/jwt/v5`](https://github.com/golang-jwt/jwt)
  - OAuth2 (Google & GitHub): [`golang.org/x/oauth2`](https://pkg.go.dev/golang.org/x/oauth2)
  - Driver: [`go.mongodb.org/mongo-driver/v2`](https://go.mongodb.org/mongo-driver/v2)
- **Frontend:** TypeScript
- **Database:** MongoDB (hosted in a GCP cluster for low-latency access)
- **Deployment:** GCP Cloud Run as `hammergen`

## Development

*Project structure and setup instructions will be updated as modules are implemented.*
