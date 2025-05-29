docker login reg.home.cloudgeni.us
docker buildx build -t reg.home.cloudgeni.us/ollama-docker . --push

docker compose -f docker-compose-ollama-gpu.yaml up -d --force-recreate


docker compose exec -it ollama ollama pull ollama:3.3
docker compose exec -it ollama ollama pull mixtral:8x7b
docker compose exec -it ollama ollama pull codellama:7b-instruct

docker exec -it ollama ollama run llama3.3 --format json "What is the capital of France?"

docker exec -it ollama ollama run mixtral:8x7b --format json "What is the capital of France?"