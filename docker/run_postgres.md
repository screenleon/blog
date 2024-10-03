# Run Postgres
================================

**Author**: Lien Chen  **Date**: 2024-10-03

### Running Postgres Container

To run a Postgres container on Docker, use the following command, replacing `CONTAINER_NAME` with your desired container name and `YOUR_PASSWORD` with your desired password:

```bash
docker run --name "CONTAINER_NAME" -e POSTGRES_PASSWORD="YOUR_PASSWORD" -d postgres
```

---

### Adding a GUI for Easy Management

For a more user-friendly experience, you can add a GUI using PGAdmin. Run the following command, replacing `LOCALHOST_PORT` with your desired local port, `EXAMPLE@example.com` with your desired email, and `YOUR_PASSWORD` with your desired password:

```bash
docker run --name "POSTGRES_ADMIN" -p "LOCALHOST_PORT:80" -e "PGADMIN_DEFAULT_EMAIL=EXAMPLE@example.com" -e "PGADMIN_DEFAULT_PASSWORD=YOUR_PASSWORD" -d dpage/pgadmin4
```