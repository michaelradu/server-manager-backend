# Server Manager Backend

Spring and MySQL backend for managing servers. 

## Getting Started

* Create a new MySQL (or MariaDB) database named serverdb.
* Fill in the `src/main/resources/application.yml` username and password fields
* Run the project.

Now you can make API requests either via the [Angular Frontend](https://github.com/michaelradu/server-manager-frontend) or Postman.

All API requests go through `http://localhost:8080/server/` which I will call `$BASE` in the following examples:

## Create a new entry

`POST` to `$BASE/save` with a body such as:

```json
{
    "ipAddress": "192.168.1.195",
    "name": "Microsoft Windows",
    "memory": "32 GB",
    "type": "Lenovo",
    "status": "SERVER_DOWN"
}
```

## List existing entries

`GET` `$BASE/list`

The output should look similar to:

```json
{
    "timeStamp": "2022-08-05T14:19:02.708516",
    "statusCode": 200,
    "status": "OK",
    "message": "Servers retrieved",
    "data": {
        "servers": [
            {
                "id": 1,
                "ipAddress": "192.168.1.160",
                "name": "Ubuntu Linux",
                "memory": "16 GB",
                "type": "PC",
                "imageUrl": "http://localhost:8080/server/image/server1.png",
                "status": "SERVER_UP"
            },
            {
                "id": 2,
                "ipAddress": "192.168.1.195",
                "name": "Microsoft Windows",
                "memory": "32 GB",
                "type": "Lenovo",
                "imageUrl": "http://localhost:8080/server/image/server4.png",
                "status": "SERVER_DOWN"
            },
            {
                "id": 4,
                "ipAddress": "192.168.1.170",
                "name": "Arch Linux",
                "memory": "32 GB",
                "type": "PC",
                "imageUrl": "http://localhost:8080/server/image/server1.png",
                "status": "SERVER_UP"
            }
        ]
    }
}
```

## Ping an entry

`GET` `$BASE/ping/{ipAddress}`

Where `{ipAddress}` is IP you wish to ping.

## Delete an entry

`DELETE` `$BASE/delete/{id}`

Where `{id}` is the id of the server you wish to delete.