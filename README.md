# chat

## Contexte

Fork de ce repo [dont l'issue ne se résoudra pas toute seule](https://github.com/m1k1o/chat/issues/32)

## recorder.getBlob()
 - là dedans on dirait y'a le son, essayer de faire une recherche d'un player javascript construit par appendHTML etc ? Genre comme replace audio mais qui en refait un à chaque message ?

## À suivre
 - d'abord récupérer le lien du blob ? Envoyer tout balises etc depuis replaceAudio mauvaise méthode ?
 - bug d'autoplay dans firefox ?
 - The Notification permission may only be requested from inside a short running user-generated event handler. ?
 - osef des gens connecté·xs et de leurs pseudos ?
 - faire un feedback interactif du preview son pour pas l'envoyer en s'étant trompé ?
 - transformer le bouton en « VRAIMENT ENVOYER » ?
 - réussir à mettre le son dans un message
 - pistes : comprendre comment envoyer des trucs dans le var Chat ?

## Historique du repo de base

Simple plug & play real-time JavaScript chat implemented using Socket.io.

Where simplicity meets usability:

* No user accounts - just enter nickname and join.
* No history saved by default - only logged-in users can see recent history.
* No configuration.
* Only one room - you can't create any other rooms or write PM to others.
* Files sharing is possible - without storing any data on server.
* Emojis - just a few of them.

![screenshot](https://raw.githubusercontent.com/m1k1o/chat/master/screenshot.png)

## docker

```sh
docker run -d \
	--name chat \
	-p 80:80 \
	m1k1o/chat:latest
```

## docker-compose

```yml
version: "3"
services:
  chat:
    image: m1k1o/chat:latest
    restart: unless-stopped
    ports:
      - 80:80
    environment:
      CACHE_SIZE: 50 # optional: message count stored. Defaults to zero.
 ```

## Cache
`CACHE_SIZE` is optional and determines the number of messages stored on the server. When new users join (or reconnect), that cache is sent to give a brief history. This defaults to zero, but can be set as an environment variable.

If you're not running in a docker container, you can make a `.env` file in the project root with `CACHE_SIZE=50` in.

Note: This cache will be text or images so be mindful not to set it too high as it could be n images sent to every new user.

## How to install

Requirements: `nodejs`, `npm`

1. Clone this repository.
	- `git clone https://github.com/m1k1o/chat .`
2. Install server dependencies.
	- `npm install`
3. Run server (default port is `80`).
	- `npm start [custom_port]`
    - si merde avec nodejs : `ln -s /usr/bin/node /usr/local/bin/nodejs`
4. Done, visit your chat in browser.
