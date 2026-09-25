# Star

A Discord bot for the Rutgers CS community. Members earn XP by chatting, level up, and compete on server leaderboards.

Built with Java 21, JDA, and SQLite. Deployed to AWS EC2 with Docker and GitHub Actions.

## Commands

- `/rank [member]` — view level, XP, and server rank
- `/leaderboard` — top 10 members by XP
- `/ping` — check bot latency

## Run locally

Requires Java 21 and Maven.

Copy `config.example.properties` to `config.properties` and add your bot token.

```bash
mvn package
java -jar target/star.jar
```

Run tests with `mvn test`.

See [deployment instructions](docs/DEPLOYMENT.md) for hosting setup.

## License

[MIT](LICENSE)
