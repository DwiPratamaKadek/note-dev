**Pake Cek isi Db**

```bash 
    docker exec -it mydb-db-1 mysql -u root -p
```
**Meliat database dan isi table**
```bash 
    SHOW DATABASES;
    USE nama_database;
    SHOW TABLES;
    SELECT * FROM users;
```

**Membuat  Migration**
```bash 
    npx sequelize-cli migration:generate --name nama-model
```

**Membuat Migration dan Model**
```bash 
    npx sequelize-cli model:generate --name User --attributes name:string,email:string
```

**Jalankan Migration**
```bash 
    npx sequelize-cli db:migrate

```
**Melakukan rollBack Migration**
```bash 
    npx sequelize db:migrate:undo:all 
```

**Untuk melakukan migration di container docker**
```bash 
    docker compose exec nama_container npx sequelize-cli db:migrate
```


## Setup Sequelize + docker 

**install dulu sequelize-cli nya**
```bash 
    npm install --save-dev sequelize-cli
```

**setup menggunakan folder src/**
setup ini berfungsi supaya si abang sequelize mengetahui pathnya dimana 
```bash 
    .sequelizerc

    const path =  require("path")

    module.exports = {
        config:path.resolve("src/config/config.json"),
        "models-path":path.resolve("src/models"),
        "migrations-path":path.resolve("src/migrations"),
        "seeders-path":path.resolve("src/seeders")
    }

```
**kemudian run seperti ini**
```bash 
    docker compose exec backend npx sequelize-cli db:migrate
```
**setting untuk db congfig** 
di sini kita menggunakan docker, jadi mengikuti service pada docker. 

```bash 
    {
        "development": {
            "username": "root",
            "password": "root",
            "database": "note-app",
            "host": "db",
            "dialect": "mysql"
        },
        "test": {
            "username": "root",
            "password": "root",
            "database": "note-app",
            "host": "db",
            "dialect": "mysql"
        },
        "production": {
            "username": "root",
            "password": "root",
            "database": "note-app",
            "host": "db",
            "dialect": "mysql"
        }
    }

```




## Commend Docker compose 

1. **Restart Docker Compose**
```bash 
    docker compose restart
```
2. **Start Service Docker Compose**
```bash 
    docker compose up 
    atau 
    docker compose up -d
```
3. **Hapus Service pada container Docker Compose**
```bash 
    docker compose down
```
4. **Stop service Docker Compose**
```bash 
    docker compose stop
```
5. **Build ulang Image (jika ada perubahan pada docker file)**
```bash 
    docker compose build
```
6. **Cek Status Docker Compose yang jalan**
```bash 
    docker compose p
```