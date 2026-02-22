1. 建置 Docker Image
docker compose build --no-cache
2. 建置 Docker network
docker network create dev-network || true
3. 建置 Docker container
docker compose up -d