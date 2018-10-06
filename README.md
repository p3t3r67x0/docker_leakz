# docker_leakz

Docker repository to build leakz website and API


## Prerequisites

First you must clone the repository and then change directory.

```sh
git clone git@github.com:webtobesocial/docker_leakz.git
cd docker_leakz
```

First things first. There are some steps you might do to run the container. You must create `create_user.js` file in the **mongodb** folder. Then you want to replace `<password>` with your own password.

```js
db.createUser({user: "admin", pwd: "<password>", roles: [{ role: "userAdminAnyDatabase", db: "admin" }] })
db.createUser({user: "pymongo", pwd: "<password>", roles: [{ role: "readWrite", db: "intel" }] });
```

Next you must create a `.secret` file in the **frontend** folder. Then you want to replace `<password>` with your own password which must be the same as the above password you choose.

```js
<password>
```

Then you create a `.config` file in the same **frontend** folder.

```js
{
    "db_name": "intel",
    "db_uri": "mongodb",
    "db_port_mails": "27017",
    "db_port_passwords": "27017"
}
```


## Build

Now you are ready to run following commands from your shell.

```sh
docker-compose build --no-cache
docker-compose up -d
```

Now you may run `docker ps` to verify that all three containers are up and running. Next we want to execute the following command. Make sure to replace `<password>` with your choosen password some steps above.

```sh
docker exec docker_leakz_mongodb_1 bash -c "mongo intel --authenticationDatabase admin -u admin -p <password> create_user.js"
```

Then you should be able to open the website under http://127.0.0.1:8000/


## Debugging

Try to run the following command from your host system.

```sh
docker logs docker_leakz_mongodb_1
docker logs docker_leakz_frontend_1
docker logs docker_leakz_nginx_1
```

Don't hesitate to contact me [@webtobesocial](https://twitter.com/webtobesocial) with your question.
