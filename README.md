---
topic: sample
languages:
  - python
products:
  - azure
  - azure-cosmos-db
---

# Build a Flask app using Azure Cosmos DB for MongoDB API

This content was taken from [this repo](https://github.com/Azure-Samples/CosmosDB-Flask-Mongo-Sample) as a demonstration of how we can update the samples template to provide more context to developers.

This sample shows you how to use the Azure Cosmos DB for MongoDB API to store and access data from a Flask application.

## Prerequisites

- Download the [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator). The emulator is currently only supported on Windows.
- Install [Visual Studio Code](https://code.visualstudio.com/Download) for your platform.
- Install the Don Jayamanne's [Python Extension](https://marketplace.visualstudio.com/items?itemName=donjayamanne.python)

## Getting started

1. Clone or download this sample repository
3. Run the following command to install the required Python modules in the context of the sample folder.
    ```bash
    pip install -r .\requirements.txt
    ```
4. Open the sample folder in Visual Studio Code or your IDE of choice.

## Run the sample

1. Make sure the Azure Cosmos DB Emulator is running.
2. Open a terminal window and `cd` to the directory that the app is saved in.
3. Set the environment variable for the Flask app with `set FLASK_APP=app.py` on Windows, or `export FLASK_APP=app.py` if you are using macOS.
4. Run the app with `flask run` and point your browser to `http://127.0.0.1:5000/`.
5. Add and remove tasks and see them added and changed in the collection.

## Deploy to Azure

To deploy this app, you can create a new web app in Azure and enable continuous deployment with a fork of this GitHub repo. Follow the [App Service continuous deployment tutorial](https://docs.microsoft.com/azure/app-service-web/app-service-continuous-deployment) to set up continuous deployment with GitHub in Azure.

When deploying to Azure, you should remove your application keys and make sure the section below is not commented out:

```python
    client = MongoClient(os.getenv("MONGOURL"))
    db = client.test    #Select the database
    db.authenticate(name=os.getenv("MONGO_USERNAME"),password=os.getenv("MONGO_PASSWORD"))
```

You then need to add your MONGOURL, MONGO_PASSWORD, and MONGO_USERNAME to the application settings. You can follow the [website configuration tutorial](https://docs.microsoft.com/azure/app-service-web/web-sites-configure#application-settings) to learn more about Application Settings in Azure Web Apps.
