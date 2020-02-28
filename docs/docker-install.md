## Установить docker

- Установил необходимые пакеты, которые позволяют apt подключаться к репозиториям по HTTPS:

```bash
sudo apt-get update  
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

- Добавил в свою систему ключ GPG официального репозитория Docker

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```

- Провил ключ (должен быть docker)

```bash
sudo apt-key fingerprint 0EBFCD88
```

- Добавил репозиторий Docker в список источников пакетов APT

```bash
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

- Обновил индекс пакетов apt

```bash
sudo apt-get update
```

- Следует убедиться, что мы устанавливаем Docker из репозитория Docker, а не из репозитория по умолчанию debian (ссылки должны вести на репо docker)

```bash
apt-cache policy docker-ce
```

- Установил docker

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

- Добавил текущего пользователя в группу docker

```bash
sudo usermod -aG docker ${USER}
```

- Применил изменения в группе (так же можно просто перезайти в консоль)

```bash
exec newgrp docker
```

- Убедился, что пользователь добавлен в группу docker

```bash
id -nG
```

- Проверил версию docker и его работоспособность

```bash
docker version
docker run hello-world
```

## Установить docker-compose

- Задал необходимые переменные

```bash
COMPOSE_VER=1.25.4
SHA_SUM=542e93b1d5106d2769b325f60ba9a0ba087bb96e30dc2c1cb026f0cb642e9aed
```

- Скачал бинарник

```bash
curl -L https://github.com/docker/compose/releases/download/${COMPOSE_VER}/docker-compose-$(uname -s)-$(uname -m) -o docker-compose

```

- Проверил контрольную сумму

```bash
echo $SHA_SUM docker-compose | sha256sum -c -
```

- Переместил бинарник в PATH дал ему права на выполнение и проверил версию

```bash
sudo mv docker-compose /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose version
```
