# mlflow-backend-and-server
Example MLFlow server and backend. (QB AA 5th Meetup: "Machine Learning Lifecycle with Kedro and MLFlow")

## System Requirements

[Docker](https://docs.docker.com/desktop/)
[Docker Compose](https://docs.docker.com/compose/install/)

## Install python deps

Either create a new env (python>=3.7)
```
conda env create -f conda.yml
```
or install from requirements.txt
```
pip install -r requirements.txt
```

## Spin up the backend of the mlflow server (a mysql db server)

after setting the environment variables in `.env` (`source .env`)

```
docker-compose
```

## Running the MLFlow server

On a new terminal (`source .env` if necessary)

```
mlflow server --backend-store-uri mysql+pymysql://root:${MYSQL_ROOT_PASSWORD}@localhost:${MYSQL_PORT}/${MYSQL_DATABASE}  --host 0.0.0.0 --default-artifact-root <path to directory to store artifacts>
```

example:

```
mlflow server --backend-store-uri mysql+pymysql://root:${MYSQL_ROOT_PASSWORD}@localhost:${MYSQL_PORT}/${MYSQL_DATABASE}  --host 0.0.0.0 --default-artifact-root `pwd`/mlruns
```

On a browser go to `http://localhost:5000`

![mflow server](mlflow-server.png)
