# Gemini Agent Guide - 5e-hammergen

## Project Overview
**5e-hammergen** is a character generator and campaign/rules tool for Warhammer Fantasy Roleplay (WFRP / TTRPG systems).
This project is an evolution and iteration of [wfrp-hammergen](https://github.com/jmilosze/wfrp-hammergen) (located locally at `../wfrp-hammergen`).

## Tech Stack & Tooling
- **Backend:** Go (Golang) - high-performance API, domain logic, character generation rules, data persistence.
- **Frontend:** TypeScript - modern, reactive frontend application with type-safe state management and UI components.
- **Development Environment:** JetBrains IDEs (GoLand, WebStorm, IntelliJ IDEA).
- **Workflow:** Rapid iteration and vibecoding with AI pair programming.

## Project Structure (Target)
```
5e-hammergen/
├── GEMINI.md           # Agent rules and context guide
├── README.md           # Project documentation
├── .gitignore          # Git ignore rules for Go, TypeScript, JetBrains
├── backend/ (or api/)  # Go backend services & domain logic
└── frontend/ (or web/) # TypeScript frontend application
```

## Guiding Principles & Conventions
1. **Domain & Rules Accuracy:** Maintain high fidelity to tabletop RPG mechanics (stats, careers, species, talents, spells, skills, inventory).
2. **Type Safety & Modularity:** Ensure shared data structures and schemas between backend and frontend are clear, consistent, and strictly typed.
3. **Idiomatic Go:** Follow standard Go project layout, clean error handling, proper interface usage, and comprehensive unit tests.
4. **Modern TypeScript:** Enforce strict typing, clean component architecture, and responsive UI.
5. **Pair Programming / Vibecoding Style:**
   - Proactive, concise, and focused implementations.
   - Respect JetBrains IDE and local developer tooling.
   - Reference previous iteration patterns in `../wfrp-hammergen` when useful for domain rules or data models, but modernize and improve architecture where appropriate.
