package main

import (
	"fmt"
	"log"
	"time"

	"github.com/eclipse/paho.mqtt.golang"
	"github.com/go-redis/redis"
)

func main() {
	client := redis.NewClient(&redis.Options{
		Addr: "localhost:6379",
	})
	_, err := client.Ping().Result()
	if err != nil {
		log.Fatal(err)
	}

	opts := mqtt.NewClientOptions().AddBroker("tcp://localhost:1883").SetClientID("mqtt-to-redis")
	clientMQTT := mqtt.NewClient(opts)
	if token := clientMQTT.Connect(); token.Wait() && token.Error() != nil {
		log.Fatal(token.Error())
	}

	clientMQTT.Subscribe("my-topic", 0, func(client mqtt.Client, msg mqtt.Message) {
		client.Publish("redis-channel", 0, false, msg.Payload())
		fmt.Println("Message forwarded to Redis")
	})

	time.Sleep(1 * time.Hour)
}

