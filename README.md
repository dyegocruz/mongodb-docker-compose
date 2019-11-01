# Docker
# Set NODE_ENV para o ambiente selecionado e ele carregará as variáveis corretamente.

```
$ chmod +x start.server.sh 

```

# Em caso de ser necessário autenticação de usuário seguir o passo a passo abaixo.

### Adicionar as linhas abaixo no docker-compose.yml

```

environment:
  - MONGO_INITDB_DATABASE=${NODE_ENV}
  - MONGO_INITDB_ROOT_USERNAME=mongoadmin
  - MONGO_INITDB_ROOT_PASSWORD=secret

```

### Iniciar o container com o comando abaixo

```
$ ./start.server.sh
```

### Executar os comandos abaixo para criação do usuário que será criado e utilizado

```

$ docker ps

$ docker exec -it CONTAINER ID bash

$ mongo

$ use admin

$ db.auth(MONGO_INITDB_ROOT_USERNAME, MONGO_INITDB_ROOT_PASSWORD)

$ db.createUser(
  {
    user: "usuario",
    pwd: "password",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
  }
)

```