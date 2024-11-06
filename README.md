# LocalAI
This repository contains the Docker Compose configuration and .env file to set up a local AI development environment with the following services:

- Ollama (11434:11434)
- Open-WebUI (3000:8080)
- n8n (5678:5678)
- Postgres (5432:5432)
- Qdrant (6333:6333)
- Lobe-Chat (3210:3210)
- SearXNG (8088:8080)

## Getting Started
- Install Docker Desktop
- Install GitHub Desktop
1. Create folder for the project on your pc and open this in your terminal (you can open in explorer, right click > Open in Terminal).
2. Pull this Github repo: `git pull https://github.com/5capeg0at/LocalAI master`
3. Rename the file dotenv.example to .env - `cp .env.example .env`
4. a) To run in CPU only mode, and run `docker compose --profile cpu up -d` OR
   b) If you have a GPU available and want to utilise it, run `docker compose --profile gpu-nvidia up -d`

After the services are up and running, you might need to manually pull the models for Ollama. You can do this by following these steps:
  Go to the Ollama container in Docker Execute the following commands to pull the models:
    `ollama pull llama3.2:3b` `ollama pull nomic-embed-text`
#### Tip
  You can interact with ollama in your Terminals (including VSCode) with the command `docker exec {name of container} {command}`
  i.e. Use `docker exec ollama ollama list` to see what models are pulled and ready.
  Feel free to customise, just pull more models, they are found here: [https://ollama.com/library](https://ollama.com/library)

## Access
You can now access the services at the following URLs:

- Open-WebUI: [http://localhost:3000](http://localhost:3000/)
- Lobe-Chat: [http://localhost:3210](http://localhost:3210/)
- Ollama: [http://localhost:11434](http://localhost:11434/)
- n8n: [http://localhost:5678](http://localhost:5678/)
- SearXNG: [http://localhost:8088](http://localhost:8088)

The other services (Postgres, Qdrant) can be accessed on their respective ports, but there is no UI - these are for n8n automations and RAG.

## Usage
- The main UI you'll likely use is Open-WebUI, which provides a web-based interface to interact with the Ollama model. You can select the model you've imported in the previous step from the dropdown. 
- The Lobe-Chat service is included in this setup, but I'm still working on how to properly use it. Feel free to explore and experiment with it.
- Web Search via SearXNG is enabled, click the plus icon left of your chat line to turn it on for your prompt (until I figure out how to keep it enabled by default).

## Knowledge/RAG
Open-WebUI has a built in RAG (Retrieval Augmented Generation) support, just go to Workspace > Knowledge to upload documents, reference them with # in your prompt. 

I am looking at n8n workflows and R2R ([RAG 2 Riches](https://github.com/SciPhi-AI/R2R)) to implement better scalable RAGs, as I'm unsure how Open-WebUI will perform. 


## Contributing

If you encounter any issues or have suggestions for improvement, please feel free to open an issue or submit a pull request.
