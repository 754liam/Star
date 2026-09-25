# Star

Star is a Discord bot for the Rutgers CS community that tracks activity using an XP and leveling system.

## Features

- Earn XP by sending messages
- 60-second XP cooldown per user
- Quadratic leveling system
- Per-server leaderboards
- Level-up announcements
- SQLite persistence
- Dockerized deployment to AWS EC2

## Commands

- `/rank [member]` — View level, XP, progress, and server rank
- `/leaderboard` — View the top 10 members by XP
- `/ping` — Check bot latency

## Tech Stack

Java 21, JDA, SQLite, Maven, Docker, GitHub Actions, and AWS EC2.

## Running Locally

```bash
cp config.example.properties config.properties
mvn test
mvn package
java -jar target/star.jar
```

Add your Discord bot token to `config.properties` before running.

## Deployment

GitHub Actions runs tests and builds the Docker image on every push. Pushes to `main` deploy the latest version to EC2.

See `docs/DEPLOYMENT.md` for setup instructions.

## License

MIT
