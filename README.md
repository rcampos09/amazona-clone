# Amazona-clone ECommerce Website
Final project mern (amazona-clone) in order to dockerize and deploy in GCP (GKE) in cluster varying everything learned in the course of (Docker-Kubernetes)

## Demo Website
- 👉 GKE : [http://34.75.232.198/](http://34.75.232.198/)


## Example Website

![ Image 2](/images/2.png)


## You Will Learn

- Run project in local
- Run project in docker-compose
- Run project in GKE

### Firts Clone repo

```
$ git clone https://github.com/rcampos09/amazona-clone
$ cd amazona-clone
```


## Run Locally

### 1. Setup MongoDB opcional

- Docker MongoDB 
  - [https://hub.docker.com/_/mongo](https://hub.docker.com/_/mongo)
  
- Atlas Cloud MongoDB
  - Create database at [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
  - Create .env file in root folder
  - Set DBUSER= user data base in Mongo Atlas
  - Set DBPASSWORD= password data base Mongo Atlas
  - Set DBNAME= name data base Mongo Atlas

Note: in backend (server.js) connection for local check url of mongo for replace

### 2. Run Backend

```
$ npm install
$ npm run start
```

### 3. Run Frontend

```
# open new terminal
$ cd frontend
$ npm install
$ npm run start
```

## Run Locally Docker-Compose

### 1. Setup MongoDB Opcional

- Atlas Cloud MongoDB 
  - Create database at [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
  - Create .env file in root folder
  - Set DBUSER= user data base in Mongo Atlas
  - Set DBPASSWORD= password data base Mongo Atlas
  - Set DBNAME= name data base Mongo Atlas
- Docker MongoDB 
  - [https://hub.docker.com/_/mongo](https://hub.docker.com/_/mongo)
  - Create .env file in root folder
  - Set MONGODB_URL_LOCAL=mongodb://localhost/amazona  

Note: Check .env-example for configure Opcion mongo

### 2. Run docker-compose

```
# open new terminal
$ docker-compose up -d --build
```

Note: Check in folder frontend file nginx.conf for using docker compose

## Run Deployment (GKE) GCP

### 1. Setup MongoDB Opcional

- Atlas Cloud MongoDB 
  - Create database at [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
  - Set DBUSER= user data base in Mongo Atlas
  - Set DBPASSWORD= password data base Mongo Atlas
  - Set DBNAME= name data base Mongo Atlas
  
  Note: For configure secret using this variable

### 2. Configure Cluster (GKE) GCP for using in local

- Create Account in GCP (free)
  - [https://cloud.google.com/free/docs/gcp-free-tier](https://cloud.google.com/free/docs/gcp-free-tier)
- Enable Api-Services
  - [https://cloud.google.com/apis?hl=es-419](https://cloud.google.com/apis?hl=es-419)
- Create Cluster (default)
  - [https://cloud.google.com/kubernetes-engine](https://cloud.google.com/kubernetes-engine)
- Install and connection gcloud in local
  - [https://cloud.google.com/sdk/docs/install](https://cloud.google.com/sdk/docs/install)

    ```
    gcloud init
    ```
- Connection
    ```
    gcloud auth configure-docker
    ```
- Connection cluster (GKE) to Local
    ```
    gcloud container clusters get-credentials (name-cluster) --zone us-east1-b --project (name-project-id)
    ```

### 3. Create images and push to (Container Registry) GCP from local

- Create Images Local

    ```
    cd path ./
    docker build -t us.gcr.io/name-project-id/backapp .
    ```

    ```
    cd path ./front
    docker build -t us.gcr.io/name-project-id/frontapp .
    ```
- Push images to GCP

    ```
    cd path ./
    docker push us.gcr.io/name-project-id/backapp
    ```

    ```
    cd path ./front
    docker push us.gcr.io/name-project-id/frontapp
    ```
### 4. Create namespace (GKE) GCP

    ```
    cd path ./
    kubectl create namespace amazona
    ```

### 5. Create secret (GKE) GCP Opcional

- Create secret for Mongo Atlas 
    ```
    kubectl create secret generic db-credentials \
    --from-literal=DBUSER=DBUSER \
    --from-literal=DBPASSWORD=DBPASSWORD \
    --from-literal=DBNAME=DBNAME \
    --from-literal=JWT_SECRET='secretJWT12345' -n amazona
    ```
- Create secret for Mongo local pod
  ```
    kubectl create secret generic db-credentials \
    --from-literal=MONGODB_URL_LOCAL=mongodb://mi-servicio-mongo.amazona.svc.cluster.local:27017 \
    --from-literal=JWT_SECRET='secretJWT12345' -n amazona
    ```

### 6. Create and apply Service Account (GKE) GCP

- Create secret for Mongo Atlas or Mongo local Pod
    - Install it from [https://cloud.google.com/iam/docs/creating-managing-service-accounts](https://cloud.google.com/iam/docs/creating-managing-service-accounts)

    ```
    gcloud auth activate-service-account user-gke-service-accounts@testkubernetes-01.iam.gserviceaccount.com --key-file=secret-user-sa.json
    ```

### 7. Apply deployment (GKE) GCP Opcional

- Apply deployment using Mongo Local

    ```
    ./backend
    kubectl apply -f deployment-localDB.yaml
    ```
    ```
    ./fronted
    kubectl apply -f deployment.yaml
    ```
    ```
    ./
    kubectl apply -f deployment.yaml
    ```
- Apply deployment using Mongo Cloud

    ```
    ./backend
    kubectl apply -f deployment-cloudDB.yaml
    ```
    ```
    ./fronted
    kubectl apply -f deployment.yaml
    ```
### 8. Check ip services app (website)

  ![ Image 1](/images/1.png)


## Seed Users and Products

- Run this on chrome: http://localhost:5000/api/users/seed
- It returns admin email and password
- Run this on chrome: http://localhost:5000/api/products/seed
- It creates 6 sample products

## Admin Login

- Run http://localhost:3000/signin 
- Enter admin email and password and click signin

Note: Opcional port if you using in local or if you deploment delete port.

### TASK Evaluation Project final

- [x] Repositorio
- [x] Léeme
- [x] Dockerfile
- [x] Persistencia de archivos
- [x] Persistencia de datos
- [x] Kubernetes
- [x] Container Registry
- [x] Entorno
- [x] Service Account
- [x] Frontend
- [x] Subida de Archivos
- [x] Servicios
- [x] Docker build
- [x] Pod
- [x] Secretos
- [x] Migraciones

**Free Software, Hell Yeah!**

> Created for evaluation escalab course (Docker-Kubernetes)

> Link: https://escalab.academy/docker-kubernetes.html

> Teacher: Alberto Zenteno

> github : https://github.com/Zenteno