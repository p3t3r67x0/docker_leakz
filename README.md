# docker_leakz

Docker repository to build leakz website and API


## Prerequisites

First there are some steps you might do to run the container.
You must create `create_user.js` file in the mongodb folder.

```js
db.createUser({user: "admin", pwd: "<password>", roles: [{ role: "userAdminAnyDatabase", db: "admin" }] })
db.createUser({user: "pymongo", pwd: "<password>", roles: [{ role: "readWrite", db: "intel" }] });
```

Next you must create a `.secret` file in the frontend folder.

```js
<password>
```

Then you create a `.config` file in the same frontend folder.

```js
{
    "db_name": "intel",
    "db_uri": "mongodb",
    "db_port_mails": "27017",
    "db_port_passwords": "27017"
}
```

Now you are ready to run following commands.

```sh
docker-compose build --no-cache
docker-compose up -d
```

Now you may run `docker ps` to verify that all three containers are up and running.
Then you should be able to open the website under http://127.0.0.1:8000/
