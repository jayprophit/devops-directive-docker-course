DATABASE_URL:=postgres://postgres:foobarbaz@localhost:5432/postgres

.PHONY: run-postgres
run-postgres:
    @echo Starting postgres container
    -docker run \
        -e POSTGRES_PASSWORD=foobarbaz \
        -v pgdata:/var/lib/postgresql/data \
        -p 5432:5432 \
        --name postgres \
        --rm \
        postgres:15.1-alpine

.PHONY: run-api-node
run-api-node:
    @echo Starting node api
    cd api-node && \
        docker build -t api-node . && \
        docker run -e DATABASE_URL=${DATABASE_URL} -p 3000:3000 --rm api-node

.PHONY: run-api-golang
run-api-golang:
    @echo Starting golang api
    cd api-golang && \
        docker build -t api-golang . && \
        docker run -e DATABASE_URL=${DATABASE_URL} -p 8080:8080 --rm api-golang

.PHONY: run-client-react
run-client-react:
    @echo Starting react client
    cd client-react && \
        docker build -t client-react . && \
        docker run -p 3000:3000 --rm client-react