# Проект по мониторингу Redis

## Инструкция по ручному запуску. Все действия выполнялись на Ubuntu 18.04.4 LTS.

### [Инструкция установке docker и docker-compose](docs/docker-install.md)

### Запуск мониторинга в docker-compose. Данные Redis, Prometheus и Grafana сохраняются в docker volumes.

- Склонировать репо

```bash
git clone https://github.com/AleksZimin/redis-monitoring.git
```

- Перейти в корень репо

```bash
cd redis-monitoring
```

- При необходимости изменить версии приложений в файле .env. ОБЯЗАТЕЛЬНО! сменить пароль от веб-интерфейса графаны в файле ./grafana/config.monitoring (параметр GF_SECURITY_ADMIN_PASSWORD)

- Запустить проект

```bash
docker-compose up -d
```

- Зайти в веб-интерфейс графаны

```bash
http://<hostname>:3000/login
```

- Ввести логин admin и пароль, который указан в параметре GF_SECURITY_ADMIN_PASSWORD в файле ./grafana/config.monitoring. Обратить внимание, что соединение не защищено! Вводить пароль только если используется доверенная сеть.


- Дашборд для Redis можно найти тут:

```bash
http://<hostname>:3000/dashboards
```

- Для появления данных необходимо подождать пару минут

### TO DO

- Использовать https для подключения к Grafana

- Защитить доступ к Redis (установить пароль)

- Написать роль на ansible для установки docker, docker-compose и последующего запуска проекта
