---
title: docker
date: 2025-04-21 17:40:39
tags:
---

```yaml
# 建立 volumes
volumes:
    db_volume: 

# 建立 services
services:

    # Container Name
    db:
        # Container image
        image: mongo
        # environment:
            # MONGO_INITDB_ROOT_USERNAME: root
            # MONGO_INITDB_ROOT_PASSWORD: root
            # MONGO_INITDB_DATABASE: app
        
        # Container Volumes
        volumes:
        - db_volume:/data/db
        # why no port forwarding?

    backend:
        # image: hw3_backend
        # Container Build folder
        build: ../backend
        # Container Port
        ports:
            - "8888:8888"
        # Container Environment
        environment:
            # Env "DB_HOST" is db :string
            DB_HOST: db
        # Container dependency: waits until the db service is started.
        depends_on:
            - db

    frontend:
        # image: hw3_frontend
        build: ../frontend
        ports:
        - "80:80"
        depends_on:
        - backend

```