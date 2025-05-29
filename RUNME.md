docker login reg.home.cloudgeni.us
docker buildx build -t reg.home.cloudgeni.us/ollama-docker . --push

docker compose -f docker-compose-ollama-gpu.yaml up -d --force-recreate

# https://www.youtube.com/watch?v=TY-ICa9S-SI

docker compose exec -it ollama ollama pull llama3.2
docker compose exec -it ollama ollama pull llama3.3
docker compose exec -it ollama ollama pull mixtral:8x7b
docker compose exec -it ollama ollama pull codellama:7b-instruct
docker compose exec -it ollama ollama pull falcon:7b
docker compose exec -it ollama ollama pull falcon:40b
docker compose exec -it ollama ollama pull qwen3:8b
docker compose exec -it ollama ollama pull gemma3:12b






docker exec -it ollama ollama run llama3.2 --verbose --format json "What is the capital of France?"

docker exec -it ollama ollama run codellama:7b-instruct --verbose --format json "What is the capital of France?"

docker exec -it ollama ollama run mixtral:8x7b --verbose --format json "What is the capital of France?"

docker exec -it ollama ollama run gemma3:12b --verbose --format json "What is the capital of France?"

docker exec -it ollama ollama run qwen3:8b --verbose --format json "What is the capital of France?"
docker exec -it ollama ollama run falcon:7b --verbose --format json "What is the capital of France?"
docker exec -it ollama ollama run falcon:40b --verbose --format json "What is the capital of France?"


