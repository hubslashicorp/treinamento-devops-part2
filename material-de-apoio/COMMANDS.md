#DOCKER-MACHINE:

If you are running macOS:

```
  $ base=https://github.com/docker/machine/releases/download/v0.16.0 &&
  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/usr/local/bin/docker-machine &&
  chmod +x /usr/local/bin/docker-machine
```

If you are running Linux:

```
  $ base=https://github.com/docker/machine/releases/download/v0.16.0 &&
  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
  sudo mv /tmp/docker-machine /usr/local/bin/docker-machine &&
  chmod +x /usr/local/bin/docker-machine
```

If you are running Windows with Git BASH:

```
  $ base=https://github.com/docker/machine/releases/download/v0.16.0 &&
  mkdir -p "$HOME/bin" &&
  curl -L $base/docker-machine-Windows-x86_64.exe > "$HOME/bin/docker-machine.exe" &&
  chmod +x "$HOME/bin/docker-machine.exe"
```

#LISTA-DE-COMANDOS:

## verifica versao do docker-machine

```$ docker-machine version```

## Ajuda com comandos

```$ docker-machine --help```

## Criando DockerHost no virtualbox

```
$ docker-machine create --driver "virtualbox" node0

$ docker-machine create --driver "virtualbox" node1

$ docker-machine create --driver "virtualbox" node2
```

## Verificando informaçoes do DockerHost

``` $ docker-machine env node0```

## listando DockerHost disponiveis

``` $ docker-machine ls```

## Parando DockerHost

```$ docker-machine stop```

## Iniciando DockerHost

```$ docker-machine start```

## Removendo DockerHost

```$ docker-machine rm ```

## Acessando DockerHost remoto

```$ docker-machine ssh node0```

## Iniciando swarm cluster remoto no DockerHost

```$ docker-machine ssh node0 docker swarm init --advertise-addr ${NODE_IP}```

## Ingressando no swarm cluster

```$ docker-machine ssh node1 docker swarm join --token SWMTKN-1-1gm0yq5x0lcid3h7nieyae2pbnqhmikvxw55hy74ty7levm1ca-6qxb9dusm8pjzo0vsz3nvskjs 192.168.99.103:2377```

## Ingressando no swarm cluster

```$ docker-machine ssh node2 docker swarm join --token SWMTKN-1-1gm0yq5x0lcid3h7nieyae2pbnqhmikvxw55hy74ty7levm1ca-6qxb9dusm8pjzo0vsz3nvskjs 192.168.99.103:2377```

## Gera token de ingresso para o Worker

```$ docker-machine ssh node0 docker swarm join-token worker```

## Lista os nodes do cluster

```$ docker-machine ssh node0 docker node ls```

## Removendo do cluster

```
$ docker-machine ssh node0 docker node rm node2 --force
$ docker-machine ssh node0 docker swarm leave (dentro do node "node2")
```

## Promover um Worker para Manager

```$ docker-machine ssh node0 docker node promote node1```

## Despromover Manager para Worker

```$ docker-machine ssh node0 docker node demote node1```

## Escalonando servicos

```$ docker service create --replicas 1 --name srv-nginx --publish 8080:80 --update-delay 10s nginx```

## Verifica onde está o serviço

```$ docker-machine ssh node0 docker service ls```

## Escalonando serviço

```$ docker-machine ssh node0 docker service scale srv-nginx=3```

## Verifica escalonamento de serviço

```$ docker-machine ssh node0 docker service ps srv-nginx```

## Verifica o que está rodando o que está rodando no Node

```$ docker-machine ssh node0 docker node ps node2```

## Remove service

```$ docker-machine ssh node0 docker service rm srv-nginx```

## Criando senha criptografada

```$ echo "Sl@sh1c0rp2020" | docker secret create senha_mysql -```

## Criando serviço e usando senha criptografada

```$ docker service create --replicas 1 --name servidor_mysql --publish 3306:3306 --secret senha_mysql -e MYSQL_ROOT_PASSWORD_FILE=/run/secrets/senha_mysql mariadb```

## Removendo dodos os DockerHosts disponiveis

$ docker-machine rm $(docker-machine ls)
