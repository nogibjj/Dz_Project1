# IDS706_Project1

[![Python application test with Github Actions](https://github.com/nogibjj/ids-706-project-1-chang/actions/workflows/main.yml/badge.svg)](https://github.com/nogibjj/Dz_Project1/actions/workflows/main.yml)

## Overview
This project is a big data script that uses Spark to query a database. For the Spark part, this project uses Databricks. Databricks clusters are run on Microsoft Azure. To communicate with the database on Databricks, this project uses the Python Databricks library. For users to run the query, there are two options: CLI and FastAPI.

<img width="530" alt="image" src="https://user-images.githubusercontent.com/31728012/190923039-4a7a0fae-3833-43f1-8d2a-a57a49ff25c0.png">


## Diagram
![Diagram](Diagram.png)

## Scaffold
This project uses [.devcontainer](https://github.com/nogibjj/ids-706-project-1-chang/tree/main/.devcontainer) to set up a container. [requirements.txt](https://github.com/nogibjj/ids-706-project-1-chang/blob/main/requirements.txt) indicates which dependencies to use. [Makefile](https://github.com/nogibjj/ids-706-project-1-chang/blob/main/Makefile) indicates how to test and lint. It also installs the required dependencies. Just use ```make``` to install.

## Databricks and Microsoft Azure
The database of this project is kept on Databricks and Databricks is run on Microsoft Azure. Databricks is based on Apache Spark, so we can leverage its parallel nature when doing queries.

We need the following four secrests to connect and communicate with our Databrick cluster.
- ```DATABRICKS_HOST```
- ```DATABRICKS_HTTP_PATH```
- ```DATABRICKS_SERVER_HOSTNAME```
- ```DATABRICKS_TOKEN```

## Test connection
We can use ```databricks-cli``` to test connection and print clusters information. Run the following CLI command.

```
databricks clusters list --output JSON | jq
```

## Query package
This project contains a package [dblib](https://github.com/nogibjj/ids-706-project-1-chang/tree/main/dblib) that connects with and executes queries to the Databricks database.

## CLI interface
This project uses ```click``` to build a CLI interface from which users can execute queries. Use the following command.

```
./query.py cli-query
```

or

```
./query.py cli-query <--query QUERYTEXT>
```

## FastAPI inferface
This project also uses ```FastAPI``` to build a microservice that enables users to query in a RESTful way. Use the following command to start the service.

```
./app.py
```

Then visit the prompted URL, and you will see a welcome message. Attach ```/query``` to the end of the URL. You will see the query result.

## CI/CD
This project uses GitHub Actions. It is built upon each push.
