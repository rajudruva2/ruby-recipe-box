# Recipe Box API

{
  "description": "Recipe Box API is a small Ruby/Sinatra JSON API for DevOps practice."
}

## Features
- Health endpoint: `GET /health`
- List and search records: `GET /recipes` or `GET /recipes?q=term`
- Get one record: `GET /recipes/:id`
- Create a record: `POST /recipes`
- Delete a record: `DELETE /recipes/:id`
- Dockerfile and GitHub Actions CI workflow

Data is stored in memory for demo simplicity and resets when the process restarts. Do not use this demo storage pattern for production data.

## Run locally
Requires Ruby 3.3+ and Bundler.
```bash
bundle install
bundle exec ruby app.rb
```

Try:
```bash
curl http://localhost:4568/health
curl http://localhost:4568/recipes
curl -X POST http://localhost:4568/recipes \
  -H 'Content-Type: application/json' \
  -d '{"name":"Lemon Rice","ingredients":["rice","lemon"],"minutes":25}'
```

## Run with Docker
```bash
docker build -t ruby-recipe-box .
docker run --rm -p 4568:4568 ruby-recipe-box
```

## CI pipeline
GitHub Actions runs Ruby syntax checks, Minitest smoke tests, and a Docker image build on pushes and pull requests to `main`.

## DevOps practice
Use this repo to practise CI, Docker builds, image tagging, registry publishing, deployment to EC2/Kubernetes, environment variables, approvals, health checks, and rollback.
