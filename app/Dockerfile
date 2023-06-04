## BUILD STAGE ##

# Baixa a imagem alpine do golang
FROM golang:1.20.4-alpine3.18 AS builder

# Indica o directorio onde ficarao armazenados os ficheiros dentro da imagem
WORKDIR /app

# Copia os ficheiros que estao na root do projecto para a WORKDIR do container
COPY . .

# Gera o ficheiro binário executável
RUN go build -o main main.go

## RUN STAGE ##

# FROM alpine:3.18
FROM scratch

WORKDIR /app

COPY --from=builder /app/main .

# Expoe a porta 8080
EXPOSE 8080

CMD [ "/app/main" ]