# Simple Farming API Game

A web-based farming simulation game built with a GraphQL API backend and PostgreSQL database. Players manage their own virtual farms, growing crops, raising animals, and expanding their operations. The core game logic is exposed through a powerful GraphQL API, with potential for integrating legacy services via SOAP.

## Features

- **GraphQL API**: Efficient, flexible API for querying and mutating game state.
- **Player Accounts**: Individual player profiles with unique farms, inventories, and progression.
- **Resource Management**: Grow crops, raise animals, manage inventory (seeds, produce, milk, wool).
- **Economy System**: Buy seeds, animals, upgrade systems (irrigation, tools), sell produce.
- **Farm Expansion**: Unlock and expand plots, upgrade farm infrastructure.
- **Data Persistence**: Robust PostgreSQL backend for game state.
- **API Testing**: Thoroughly tested endpoints using Postman collections.

## Core Endpoints (GraphQL Schema)

### Queries
- `me: Player!` - Get the current player's profile and farm state.
- `player(id: ID!): Player` - Get details of a specific player.
- `crops: [Crop!]!` - List all available crop types.
- `animals: [Animal!]!` - List all available animal types.
- `upgrades: [Upgrade!]!` - List all available farm upgrades.

### Mutations
- `login(username: String!, password: String!): AuthPayload!` - Authenticate user and get token.
- `register(username: String!, password: String!, email: String!): AuthPayload!` - Register a new player.
- `plant(seedId: ID!, plotId: ID!): FarmPlot` - Plant a seed in a specific plot.
- `harvest(plotId: ID!): HarvestPayload` - Harvest a fully grown crop.
- `buyItem(itemId: ID!, quantity: Int!): TransactionPayload` - Buy seeds, animals, or upgrades.
- `sellItem(itemId: ID!, quantity: Int!): TransactionPayload` - Sell produce, milk, wool, etc.
- `upgradeFarm(upgradeId: ID!): UpgradeResult` - Purchase and apply a farm upgrade.
- `collectAnimalProduct(animalId: ID!): CollectPayload` - Collect milk from cows, wool from sheep, etc.

### Types (Example)
- `Player`: `id`, `username`, `gold`, `inventory`, `farmPlots`, `animals`, `farmLevel`, `experience`
- `FarmPlot`: `id`, `plotNumber`, `cropId`, `growthStage`, `isPlanted`, `plantedAt`
- `Crop`: `id`, `name`, `growthTime`, `seedCost`, `sellPrice`, `productName`
- `Animal`: `id`, `type`, `milkProduction`, `woolProduction`, `purchaseCost`, `productivity`
- `Upgrade`: `id`, `name`, `cost`, `effect`, `requiredLevel`

## Technologies Used

- **Backend Framework**: FastAPI
- **GraphQL Server**: Strawberry (or Ariadne, Graphene-Py)
- **Database**: PostgreSQL
- **Authentication**: JWT (JSON Web Tokens)
- **API Documentation**: GraphQL Playground / Altair (built-in with GraphQL server)
- **API Testing**: Postman
- **Database Interaction**: SQLAlchemy (or async alternatives like Tortoise ORM)
- **HTTP Client (for testing)**: HTTPX
- **Frontend (Optional)**: HTML, CSS, JavaScript, Tailwind CSS, Apollo Client (for GraphQL)
- **Virtual Environment**: Python venv / conda
