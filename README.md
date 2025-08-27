#HyprPong

ft_transcendence/
│── Makefile               # shortcuts: build, up, down, lint, test
│── README.md              # project overview & setup instructions
│── .env.example           # environment variables template
│── docker-compose.yml     # main infra (inside /infra or root)
│
├── infra/                 # infrastructure & deployment
│   ├── nginx/             # reverse proxy configs
│   │   └── nginx.conf
│   ├── postgres/          # init SQL scripts / volumes
│   ├── redis/             # redis.conf (for cache, ws sessions) (optinal just for speed)
│   ├── docker/            # dockerfiles for services
│   │   ├── backend.Dockerfile
│   │   ├── frontend.Dockerfile
│   │   └── game.Dockerfile
│
├── backend/               # API + WebSockets + DB
│   ├── src/
│   │   ├── app.ts
│   │   ├── main.ts
│   │   ├── config/        # db, env, logging
│   │   ├── middleware/    # guards, validation, error handler
│   │   ├── modules/
│   │   │   ├── auth/      # JWT, 2FA, OAuth
│   │   │   ├── users/     # profiles, friends, avatars
│   │   │   ├── chat/      # real-time chat
│   │   │   ├── game/      # matchmaking + API for game server
│   │   │   └── admin/     # (bonus) moderation, roles
│   │   ├── utils/         # helpers (crypto, jwt, logger)
│   │   └── prisma/        # Prisma schema if using PostgreSQL
│   └── tests/
│       ├── auth.test.ts
│       ├── chat.test.ts
│       └── game.test.ts
│
├── frontend/              # React + Vite + Tailwind
│   ├── src/
│   │   ├── assets/        # images, logos, fonts
│   │   ├── components/    # reusable UI parts
│   │   ├── pages/         # Landing, Dashboard, Profile, Game
│   │   ├── features/      # chat UI, friends list, auth forms
│   │   ├── hooks/         # custom React hooks
│   │   ├── context/       # auth provider, theme provider
│   │   └── App.tsx
│   └── public/            # static files
│
├── game/                  # Pong engine + realtime server logic
│   ├── server/            # socket server (syncs game state)
│   │   ├── index.ts
│   │   ├── rooms.ts       # manages matches
│   │   └── physics.ts     # ball & paddle physics
│   ├── client/            # game canvas in React
│   │   ├── PongCanvas.tsx
│   │   └── hooks/
│   └── tests/
│       └── game.test.ts
│
├── ai/ (optional later)   # AI opponent module
│   └── bot.ts
│
└── blockchain/ (optional later)
    ├── contracts/         # solidity smart contracts
    └── scripts/           # deploy & interact
