# Amazona ECommerce Website
Welcome to my React and Node tutorial to build a fully-functional e-commerce website exactly like amazon. Open your code editor and follow me for the next hours to build an e-commerce website using MERN stack (MongoDB, ExpressJS, React and Node.JS).

## Demo Website
- 👉 Heroku : [https://newamazona-final.herokuapp.com](https://newamazona-final.herokuapp.com)
- 👉 AWS : [https://amazona.webacademy.pro](https://amazona.webacademy.pro)

## You Will Learn

- Run project in local
- Run project in docker-compose
- Run project in GKE

## Run Locally

### 1. Clone repo

```
$ git clone git@github.com:basir/amazona.git
$ cd amazona
```

### 2. Setup MongoDB

- Local MongoDB
  - Install it from [https://www.mongodb.com/try/download/community](https://www.mongodb.com/try/download/community)
  - Create .env file in root folder
  - Set MONGODB_URL_LOCAL=mongodb://localhost/amazona  
- Docker MongoDB 
  - Install it from [https://hub.docker.com/_/mongo](https://hub.docker.com/_/mongo)
  - Create .env file in root folder
  - Set MONGODB_URL_LOCAL=mongodb://localhost/amazona  
- Atlas Cloud MongoDB
  - Create database at [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
  - Create .env file in root folder
  - Set DBUSER= user data base in Mongo Atlas
  - Set DBPASSWORD= password data base Mongo Atlas
  - Set DBNAME= name data base Mongo Atlas

### 3. Run Backend

```
$ npm install
$ npm start
```

### 4. Run Frontend

```
# open new terminal
$ cd frontend
$ npm install
$ npm start
```


## Run Locally Docker-Compose

### 1. Clone repo

```
$ git clone git@github.com:basir/amazona.git
$ cd amazona
```

### 2. Setup MongoDB

- Local MongoDB
  - Install it from [https://www.mongodb.com/try/download/community](https://www.mongodb.com/try/download/community)
  - Create .env file in root folder
  - Set MONGODB_URL_LOCAL=mongodb://localhost/amazona  
- Docker MongoDB 
  - Install it from [https://hub.docker.com/_/mongo](https://hub.docker.com/_/mongo)
  - Create .env file in root folder
  - Set MONGODB_URL_LOCAL=mongodb://localhost/amazona  
- Atlas Cloud MongoDB
  - Create database at [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
  - Create .env file in root folder
  - Set DBUSER= user data base in Mongo Atlas
  - Set DBPASSWORD= password data base Mongo Atlas
  - Set DBNAME= name data base Mongo Atlas

### 3. Run Backend

```
$ npm install
$ npm start
```

### 4. Run Frontend

```
# open new terminal
$ cd frontend
$ npm install
$ npm start
```