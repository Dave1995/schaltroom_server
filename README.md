# schaltroom_server

PostgreSQL Setup
```bash
docker pull postgres
mkdir -p $HOME/docker/volumes/postgres
docker network create pg-docker
docker run --rm --network pg-docker --name pg-docker -e POSTGRES_PASSWORD=postgres -d -p 5432:5432 -v $HOME/docker/volumes/postgres:/var/lib/postgresql/data  postgres
docker exec -it -u postgres pg-docker psql postgres -c "create role rails_dualboot_poc_development with createdb login password 'rails_dualboot_poc_development';"
docker exec -it -u postgres pg-docker psql postgres -c "create role rails_dualboot_poc_test with createdb login password 'rails_dualboot_poc_test';"
docker exec -it -u postgres pg-docker psql postgres -c "create role dualboot_prod with createdb login password 'dualboot_prod';"
```

ruby 2.3.8
```bash
bundle install
rake db:setup
rake db:migrate
rake test
```

JRuby 9.1.17.0
```bash
bundle _1.17.3_ install
rake db:setup
rake db:migrate
rake test
```
