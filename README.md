<h1 align="center">HolbertonBnB</h1>
<p align="center">An AirBnB clone.</p>

<p align="center">
  <img src="https://github.com/bdbaraban/AirBnB_clone_v2/blob/master/assets/hbnb_logo.png"
	    alt="HolbertonBnB logo">
</p>

## Description :house:

HolbertonBnB is a complete RESTful web application, integrating file and
database (MySQL) storage in a back-end API with front-end interfacing in a
clone of AirBnB. The front-end is designed using HTML5/CSS3 and is served using
Python Flask. The application is configured on a distributed system - two web
servers and one load balancer - with Nginx and HAProxy.

HolbertonBnB is still in active development, with complete functionality set to
deploy in the coming month:

* Complete integration of a RESTful API
* Full configuration of website with domain name
* Serving of dynamic content using JavaScript

<p align="center">
  <img src="https://github.com/bdbaraban/AirBnB_clone_v2/blob/master/assets/hbnb_stack.png"
	    alt="HolbertonBnB stack">
</p>


### FileStorage

The default mode.

In `FileStorage` mode, every time the backend is initialized, HolbertonBnB
instantiates an instance of `FileStorage` called `storage`. The `storage`
object is loaded/re-loaded from any class instances stored in the JSON file
`file.json`. As class instances are created, updated, or deleted, the
`storage` object is used to register corresponding changes in the `file.json`.

### DBStorage

Run by setting the environmental variables `HBNB_TYPE_STORAGE=db`.

In `DBStorage` mode, every time the backend is initialized, HolbertonBnB
instantiates an instance of `DBStorage` called `storage`. The `storage` object
is loaded/re-loaded from the MySQL database specified in the environmental variable
`HBNB_MYSQL_DB`, using the user `HBNB_MYSQL_USER`, password `HBNB_MYSQL_PWD`, and
host `HBNB_MYSQL_HOST`. As class instances are created, updated, or deleted, the
`storage` object is used to register changes in the corresponding MySQL database.
Connection and querying is achieved using SQLAlchemy.

Note that the databases specified for `DBStorage` to connect to must already be
defined on the MySQL server. This repository includes scripts
[setup_mysql_dev.sql](./setup_mysql_dev.sql) and [setup_mysql_test.sql](./setup_mysql_test.sql)
to set up `hbnb_dev_db` and `hbnb_test_db` databases in a MySQL server,
respectively.

#### update
* Usage: `update <class> <id> <attribute name> "<attribute value>"`

Updates a class instance based on a given id with a given key/value attribute
pair or dictionary of attribute pairs. If `update` is called with a single
key/value attribute pair, only "simple" attributes can be updated (ie. not
`id`, `created_at`, and `updated_at`).

```
$ ./console.py
(hbnb) create User
6f348019-0499-420f-8eec-ef0fdc863c02
(hbnb)
(hbnb) update User 6f348019-0499-420f-8eec-ef0fdc863c02 first_name "Holberton" 
(hbnb) show User 6f348019-0499-420f-8eec-ef0fdc863c02
[User] (6f348019-0499-420f-8eec-ef0fdc863c02) {'created_at': datetime.datetime(
2024, 2, 17, 21, 54, 39, 234382), 'first_name': 'Holberton', 'updated_at': date
time.datetime(2019, 2, 17, 21, 54, 39, 234382), 'id': '6f348019-0499-420f-8eec-
ef0fdc863c02'}
(hbnb)
```

## Testing :straight_ruler:

Unittests for the HolbertonBnB project are defined in the [tests](./tests)
folder. To run the entire test suite simultaneously, execute the following command:

```
$ python3 unittest -m discover tests
```

Alternatively, you can specify a single test file to run at a time:

```
$ python3 unittest -m tests/test_console.py
```

## Authors :
* **Hezron Simumba** <[Hezron Simumba](https://github.com/Hezron-Simumba)>
