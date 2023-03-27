FROM golang:latest
RUN apt-get update && \
    apt-get install -y git
WORKDIR /app 
COPY /json.go .
RUN go mod init github.com/bobiesco/Microservice-applications.git
RUN go mod tidy
RUN go build -o /json.go
EXPOSE 8080
CMD ["/json.go"]
