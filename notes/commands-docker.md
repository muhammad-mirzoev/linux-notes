# 🐳 Docker Commands & Notes

---

## 🔧 Установка и проверка
- docker --version            | версия Docker
- docker compose version      | версия Docker Compose
- systemctl status docker     | статус Docker daemon
- systemctl start docker      | запуск Docker
- systemctl enable docker     | автозапуск Docker
- docker info                 | информация о системе Docker

---

## 📦 Образы (Images)
- docker images               | список образов
- docker pull <image>         | скачать образ
- docker build -t <name> .    | собрать образ из Dockerfile
- docker build -t <name>:tag .| собрать образ с тегом
- docker rmi <image>          | удалить образ
- docker image prune          | удалить неиспользуемые образы
- docker history <image>      | история слоёв образа
- docker inspect <image>      | подробная информация об образе

---

## 📦 Контейнеры (Containers)
- docker ps                   | запущенные контейнеры
- docker ps -a                | все контейнеры
- docker run <image>          | запустить контейнер
- docker run -it <image> bash | интерактивный режим
- docker run -d <image>       | запуск в фоне
- docker start <container>    | запустить контейнер
- docker stop <container>     | остановить контейнер
- docker restart <container>  | перезапустить контейнер
- docker rm <container>       | удалить контейнер
- docker container prune      | удалить остановленные контейнеры
- docker logs <container>     | логи контейнера
- docker logs -f <container>  | live-логи
- docker inspect <container>  | подробная информация

---

## 🧠 Работа внутри контейнера
- docker exec -it <container> bash | зайти в контейнер
- docker attach <container>        | подключиться к STDOUT
- exit                              | выйти из контейнера
- docker cp <container>:<path> ./  | копировать файл из контейнера
- docker cp ./file <container>:<path> | копировать файл в контейнер

---

## 🌐 Порты и переменные окружения
- docker run -p 8080:80 <image>     | проброс портов
- docker run -e KEY=value <image>   | env-переменная
- docker run --env-file .env <image>| env из файла
- docker port <container>           | посмотреть проброшенные порты

---

## 📂 Volume и данные
- docker volume ls                  | список volume
- docker volume create <name>       | создать volume
- docker volume inspect <name>      | информация о volume
- docker volume rm <name>           | удалить volume
- docker run -v volume:/data <image>| подключить volume
- docker run -v $(pwd):/app <image> | bind mount (dev)

---

## 🌐 Сети (Networks)
- docker network ls                 | список сетей
- docker network create <name>      | создать сеть
- docker network inspect <name>     | информация о сети
- docker network rm <name>          | удалить сеть
- docker run --network <name> <image> | запуск в сети

---

## 🧱 Dockerfile (основы)
- FROM <image>                      | базовый образ
- WORKDIR /app                      | рабочая директория
- COPY . .                          | копирование файлов
- RUN <command>                     | выполнить команду
- EXPOSE 3000                       | указать порт
- CMD ["npm","start"]               | команда запуска
- ENTRYPOINT ["bash"]               | точка входа
- ENV NODE_ENV=production           | переменные окружения

---

## 🧩 Docker Compose
- docker compose up                 | запустить сервисы
- docker compose up -d              | запуск в фоне
- docker compose down               | остановить сервисы
- docker compose build              | сборка образов
- docker compose ps                 | список сервисов
- docker compose logs               | логи
- docker compose exec <service> sh  | зайти в сервис
- docker compose restart            | перезапуск

---

## 🛠 Разработка и отладка
- docker stats                      | использование ресурсов
- docker top <container>            | процессы контейнера
- docker diff <container>           | изменения ФС
- docker events                     | события Docker
- docker system df                  | использование диска
- docker system prune               | очистка всего лишнего

---

## 🚀 Best Practices
- Используй .dockerignore
- Минимизируй количество слоёв
- Используй multi-stage build
- Не запускай контейнер под root
- Один контейнер = один сервис
- ENV ≠ secrets (используй vault)

---

## 📁 Полезные файлы
- Dockerfile
- docker-compose.yml
- .dockerignore
- .env

---