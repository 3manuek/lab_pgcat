# lab_pgcat

Exploratory lab for PGCat's hash-sharding.

```bash
pipenv shell
pipenv install
export DOCKER_HOST=$(docker context inspect $(docker context show) | jq -r '.[].Endpoints.docker.Host')

ansible-playbook main.yaml

# For cleaning up
ansible-playbook main.yaml --tags clean
```


```bash
PGPASSWORD=password /Applications/Postgres.app/Contents/Versions/17/bin/pgbench -h localhost -p 15432 -U node_user -d shardpool -f pgbench-shard.sql -c 10 -T 40
```