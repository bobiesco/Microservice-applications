package main

import (
	"encoding/json"
	"fmt"
	"io/ioutil"
	"log"
	"net/http"
)

type Payload struct {
	Name string `json:"name"`
}

func main() {
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		body, err := ioutil.ReadAll(r.Body)
		if err != nil {
			log.Fatal(err)
		}

		var payload Payload
		err = json.Unmarshal(body, &payload)
		if err != nil {
			log.Fatal(err)
		}

		fmt.Println(payload.Name)
	})

	http.ListenAndServe(":8080", nil)
}

