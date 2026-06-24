# Docker Node.js MongoDB

> **FR** — Application Node.js containerisée avec Docker, connectée à MongoDB et MongoDB Express via Docker Compose. Démontre la gestion des réseaux Docker, des variables d'environnement et des volumes persistants.
>
> **EN** — Containerized Node.js application connected to MongoDB and MongoDB Express via Docker Compose. Demonstrates Docker networking, environment variables, and persistent volumes.

---

## Stack

![Node.js](https://img.shields.io/badge/Node.js-20-green?logo=nodedotjs)
![MongoDB](https://img.shields.io/badge/MongoDB-latest-green?logo=mongodb)
![Docker](https://img.shields.io/badge/Docker-Compose-blue?logo=docker)

---

## FR — Description

Ce projet illustre comment containeriser une application web et la connecter à une base de données MongoDB, le tout orchestré avec Docker Compose.

**Ce qui a été réalisé :**
- Écriture d'un `Dockerfile` pour l'application Node.js (image `node:20-alpine`)
- Passage des credentials MongoDB via des variables d'environnement Docker
- Connexion des conteneurs via un réseau Docker (`mongo-network`)
- Persistance des données MongoDB avec un volume nommé (`mongo-data`)
- Accès à l'interface d'administration MongoDB Express sur le port 8081
- Build et push de l'image vers un registre privé (Nexus)
- Déploiement multi-conteneurs avec Docker Compose

## EN — Description

This project illustrates how to containerize a web application and connect it to a MongoDB database, all orchestrated with Docker Compose.

**What was done:**
- Writing a `Dockerfile` for the Node.js application (`node:20-alpine`)
- Passing MongoDB credentials via Docker environment variables
- Connecting containers via a Docker network (`mongo-network`)
- MongoDB data persistence with a named volume (`mongo-data`)
- Accessing the MongoDB Express admin UI on port 8081
- Building and pushing the image to a private registry (Nexus)
- Multi-container deployment with Docker Compose

---

## Architecture

```
┌─────────────────────────────────────────────────┐
│                  Docker Network                  │
│                                                  │
│  ┌──────────────┐    ┌──────────────────────┐   │
│  │  my-app      │    │  mongodb             │   │
│  │  Node.js     │───▶│  port 27017          │   │
│  │  port 3000   │    │  volume: mongo-data  │   │
│  └──────────────┘    └──────────────────────┘   │
│                              │                   │
│                      ┌───────────────┐           │
│                      │ mongo-express │           │
│                      │  port 8081   │           │
│                      └───────────────┘           │
└─────────────────────────────────────────────────┘
```

---

## Project Structure

```
.
├── Dockerfile          # Node.js app image (node:20-alpine)
├── mongo.yaml          # Docker Compose (app + MongoDB + Mongo Express)
├── app/
│   ├── server.js       # Node.js application
│   └── package.json
```
