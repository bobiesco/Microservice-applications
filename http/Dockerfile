FROM golang:latest
RUN apt-get update && \
    apt-get install -y git
WORKDIR /app 
COPY /HTTP.go .
RUN go mod init github.com/bobiesco/Microservice-applications.git
RUN go mod tidy
RUN go build -o /HTTP.go
EXPOSE 8080
CMD ["/HTTP.go"]
