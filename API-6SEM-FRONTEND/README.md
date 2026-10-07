# API-6SEM-FRONTEND

Frontend of **AkaVision** — Technical Document Classifier, an integrated project between Fatec SJC and AKAER.

## Stack

- **Framework:** Vue
- **Build tool:** Vite (to be confirmed)

## Running locally

```bash
# 1. Clone the repository and open the frontend folder
git clone https://github.com/User-Standart/API-6SEM.git
cd API-6SEM/API-6SEM-FRONTEND

# 2. Install the dependencies
npm install

# 3. Set up the environment variables
cp .env.example .env
# edit .env with the local backend URL

# 4. Run in development mode
npm run dev

# 5. Production build
npm run build
```

## Contribution flow

1. Create a branch from `develop`: `feature/task-name`
2. Commits and PR titles follow [Conventional Commits](https://www.conventionalcommits.org), in English: `feat:`, `fix:`, `docs:`, `chore:`, `test:`
3. Open the PR against `develop` — requires 1 approval, green CI and a validated title
4. Always merge with **Squash and merge**

## CI

The `Frontend CI` workflow runs on every PR/push to `main` and `develop`: it installs the dependencies and runs the build.

## Links

- Main project: [API-6SEM](../README.md)
- Backend: [API-6SEM-BACKEND](../API-6SEM-BACKEND)
