# Exercise 4: Docker Networking with Multiple Containers

A Flask app, a MySQL database and a Redis cache run as three containers on one user-defined bridge network, so they can reach each other by name.

## Files

| File | Purpose |
|---|---|
| `app.py` | Flask API with an `/about` endpoint on port 5001 |
| `requirements.txt` | Python dependencies |
| `Dockerfile` | Builds the Flask image (includes `ping` for testing) |

## Steps (Windows PowerShell)

1. Build: `docker build -t flask-api .`
2. Create the network: `docker network create --driver bridge my-bridge-net`
3. Verify and inspect: `docker network ls` and `docker network inspect my-bridge-net`
4. Run MySQL: `docker run -d --name mysql --net=my-bridge-net -e MYSQL_ROOT_PASSWORD=rootpass mysql:latest`
5. Run Redis: `docker run -d --name redis --net=my-bridge-net redis:latest`
6. Run Flask: `docker run -d --name flask --net=my-bridge-net -p 5001:5001 flask-api`
7. Test the API: `curl.exe http://localhost:5001/about`
8. Test connectivity: `docker exec flask ping -c 3 mysql` and `docker exec flask ping -c 3 redis`

## Cleanup

```
docker stop mysql redis flask
docker rm mysql redis flask
docker network rm my-bridge-net
```

## Questions and answers

1. **What does the `--net` flag do?** It connects the container to the named network.
2. **How do containers on the same network talk?** By container name (Docker's built-in DNS) or by IP address.
3. **Bridge vs host network?** A bridge network gives containers a private, isolated network, while a host network shares the host's network stack directly.
4. **How do you expose a container port to the host?** Use `-p HOST_PORT:CONTAINER_PORT`, for example `-p 5001:5001`.
