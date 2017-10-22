# Mis notas (MongoDB Basics Notes)

## How to add `mongo` and `mongod` commands if windows doesn't recognize it

Go to Windows environments and add to `PATH` the location of the `mongod.exe` in this case will be: `c:\mongodb\bin` then go to `c:\` drive and create an empty folder with the name of *mongoData*.

## How to start the MongoDb server

```Shell
mongod --dbpath c:\mongoData --rest --httpinterface
```

The `--rest` keyword active the http interface

More documentation [here](http://docs.mongodb.org/ecosystem/tools/http-interfaces/#http-console)

## How to install MongoDB as a Windows service

By running the following command, where we specify explicitly where to place the logs, we will install MongoDB as a Windows Service. Make sure to run the command prompt with administrator rights.

In order to install MongoDB on Windows as a service, keeping the previously used settings is as simple as adding the --install parameter and the location of the log specified by the value of --logpath.

```shell
mongod --dbpath c:\mongoData --logpath c:\mongoData\log\log.log --install --rest --httpinterface
```

If the installation is successful, you will see *MongoDB* in the Windows Services panel.

**Note**: We need to start the service manually after the first installation.

## How to start the databases after installation

Copy the rute to the bin folder where you install MongoDB and go there using the console and there type:

```shell
mongo
```

It will default connect to the test databases.

## How to enter to the simple http interface

In mongodb you have a simple http interface where you can see  usefull administrative information about the server and the operation on all the server.

We can access with our browser using the ip address of our server in most cases will be localhost and the port number of the server plus 1000:

```html
http://localhost:28017
```

## Use db keyword to manipulate the connected database and create a non existing databases.

By default there is a special keyword to access to the databases when you are connected and that keyword is `db`.

`db` keyword is the representation to the actual connected databases.

When you use the special keyword `use` it will select the database with that name. We need to highlight that if you use the keyword to select a database that doesn't exist It will perform a selection, and when you add some collection the system will create the database for you.

```shell
> use exampleDb
switched to db exampleDb
> db
exampleDb
```

## How to insert a document to a collection databases.

First we need to remember that in mongodb shell any valid javascript code is also valid mongodb code.

Create a variable with the document that we need to insert to the collection.

```shell
> var sampleDocument = {"keyvalue" : "keycontent"};
```

Then we call to our special `db` keyword to insert the `sampleDocument` variable in the collection named *sampleCollection*.

```shell
> db.sampleCollection.insert(sampleDocument);
WriteResult({ "nInserted" : 1 })
```

If the collection does not exist it will create it for you. The same happens with the database.

## How to show all the collections in the DB

```cmd
> show collections
```

## How to see documents all data in one collection

```shell
> db.nameofyourcollection.find().pretty()
```

The `pretty` keyword is used to get a better look for JSON expression.

## How to see one document in a collection

```shell
> db.sampleCollection.findOne();
```

## How to connect without connecting to database

```shell
> mongo --nodb
```

If later I want to connect:

```shell
> var conn = new Mongo("localhost:27017");
> db = conn.getDB("test");
```

## How to delete a entire collection

```shell
> db.sampleCollection.drop()
```

Where `sampleCollection` is our collection and `drop` our function that will delete all documents in the collection

There is other method to delete collections and the function names is `remove()`, but it takes a parameters to find and delete according to the parameters

## How to show all the DBs in mongodb

```cmd
> show dbs
```

**Note**: make sure that your in the `mongo` cli to be there run `mongo`