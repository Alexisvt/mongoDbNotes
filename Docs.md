# Mis notas (MongoDB Basics Notes)

## How to start the databases after installation

Copy the rute to the bin folder where you install MongoDB and go there using the console and there type:
```shell
> mongo
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

When you use the special keyword `use` it will select the database with that name or create one for you
```shell
> use exampleDb
switched to db exampleDb
> db
exampleDb
```

## How to insert a document to a collection databases.

First we need to remember that in mongodb shell any valid javascript code is also valid mongodb code.

Create a variable with the document that We need to insert to the collection.
```shell
> var sampleDocument = {"keyvalue" : "keycontent"};
```
Then we call to our special `db` keyword to insert the `sampleDocument` variable in the collection named *sampleCollection*.
```shell
> db.sampleCollection.insert(sampleDocument);
WriteResult({ "nInserted" : 1 })
```
If the collection does not exist it will create it for you. The same happens with documents.

## How to see documents in a collection

```shell
> db.sampleCollection.find().pretty
function (){
    this._prettyShell = true;
    return this;
}
```
The `pretty` keyword is used to get a better look for JSON expression.

## How to see one document in a collection

```shell
> db.sampleCollection.findOne()
function (){
    this._prettyShell = true;
    return this;
}
```
