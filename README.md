# Sami: Social Mining Dapp

Sami is a decentralized social mining platform that allows users to earn blockchain tokens by promoting projects on Twitter. The higher the engagement on their posts, the greater their rewards from the project's token allocation.

## How Sami Works

1. **Project Campaign Registration**: Projects register campaigns on the Sami platform, allocating a specific amount of their tokens as rewards.
2. **User Onboarding**: Users register and verify their Twitter accounts on Sami.
3. **Content Creation & Submission**: Registered users post content about a campaign project on Twitter, tagging the project as required. They then submit their Twitter post link to Sami.
4. **Engagement Tracking**: Sami tracks engagement (likes, retweets, comments, etc.) on the submitted post for a set period (e.g., one week).
5. **Reward Distribution**: After the tracking period, users receive rewards from the campaign's token allocation, proportional to the engagement their post received.

## Tech Stack
- **Frontend**: React, TypeScript
- **Build Tool**: Vite
- **Linting**: ESLint (with TypeScript and React plugins)

## Getting Started

### Prerequisites
- Node.js (v16 or higher recommended)
- npm or yarn

### Installation
```bash
npm install
# or
yarn install
```

### Development
To start the development server with hot module replacement:
```bash
npm run dev
# or
yarn dev
```

### Build
To build the project for production:
```bash
npm run build
# or
yarn build
```

### Preview
To preview the production build locally:
```bash
npm run preview
# or
yarn preview
```

## Linting & Code Quality
This project uses ESLint with recommended rules for TypeScript and React. To run the linter:
```bash
npm run lint
# or
yarn lint
```

For production applications, consider enabling type-aware lint rules and additional plugins as described in the comments of `eslint.config.js`.

## Contributing
Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

---

*This project was bootstrapped with Vite + React + TypeScript.*
