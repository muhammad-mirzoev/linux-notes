# 🐘 PostgreSQL Commands & Notes (Development)

## 🔧 Установка и сервис
- psql --version                 | версия psql
- postgres --version             | версия сервера
- systemctl status postgresql    | статус сервиса
- systemctl start postgresql     | запуск PostgreSQL
- systemctl stop postgresql      | остановка PostgreSQL
- systemctl restart postgresql   | перезапуск PostgreSQL
- systemctl enable postgresql    | автозапуск

---

## 🔐 Пользователи и роли
- createuser <name>              | создать пользователя
- createuser --interactive       | интерактивное создание
- dropuser <name>                | удалить пользователя
- psql -c "\du"                  | список ролей
- ALTER USER user WITH PASSWORD 'pass'; | сменить пароль
- ALTER USER user CREATEDB;      | дать право создавать БД
- ALTER USER user SUPERUSER;     | дать права суперпользователя

---

## 🗄 Базы данных
- createdb <dbname>              | создать БД
- dropdb <dbname>                | удалить БД
- psql -l                        | список БД
- psql <dbname>                  | подключиться к БД
- \c <dbname>                    | сменить БД
- SELECT current_database();     | текущая БД

---

## 🔌 Подключение (psql)
- psql                           | подключение по умолчанию
- psql -U user                   | подключение под пользователем
- psql -h host -p 5432 -U user db | полное подключение
- psql "postgresql://user:pass@host:5432/db" | URI подключение
- \conninfo                      | информация о подключении
- \q                             | выход

---

## 📊 Таблицы и схемы
- \dt                            | список таблиц
- \dt+                           | таблицы с деталями
- \dn                            | список схем
- \d <table>                     | структура таблицы
- \d+ <table>                    | структура + детали
- SELECT * FROM information_schema.tables; | все таблицы

---

## 🧱 SQL: таблицы и данные
- CREATE TABLE users (...);      | создать таблицу
- DROP TABLE users;              | удалить таблицу
- TRUNCATE TABLE users;          | очистить таблицу
- INSERT INTO users VALUES (...);| вставка данных
- SELECT * FROM users;           | выборка данных
- UPDATE users SET ...;          | обновление данных
- DELETE FROM users WHERE ...;   | удаление данных

---

## 🔑 Индексы и ключи
- CREATE INDEX idx_name ON table(col); | создать индекс
- DROP INDEX idx_name;             | удалить индекс
- \di                              | список индексов
- PRIMARY KEY (id)                 | первичный ключ
- UNIQUE (email)                   | уникальное поле
- FOREIGN KEY (user_id) REFERENCES users(id) | внешний ключ

---

## 🧪 Транзакции
- BEGIN;                           | начать транзакцию
- COMMIT;                          | сохранить изменения
- ROLLBACK;                        | откатить изменения
- SAVEPOINT sp1;                   | точка сохранения
- ROLLBACK TO sp1;                 | откат к savepoint

---

## 📈 Отладка и анализ
- EXPLAIN SELECT ...;              | план запроса
- EXPLAIN ANALYZE SELECT ...;      | реальное выполнение
- SHOW ALL;                        | все настройки
- SHOW shared_buffers;             | настройка сервера
- SELECT version();                | версия PostgreSQL
- SELECT now();                    | текущее время

---

## 📦 Бэкапы и восстановление
- pg_dump db > backup.sql          | бэкап БД
- pg_dump -U user db > backup.sql  | бэкап под пользователем
- pg_dumpall > all.sql             | бэкап всех БД
- psql db < backup.sql             | восстановление
- pg_restore -d db backup.dump     | restore из dump

---

## 🐳 PostgreSQL + Docker
- docker pull postgres             | скачать образ
- docker run -d \
  -e POSTGRES_USER=user \
  -e POSTGRES_PASSWORD=pass \
  -e POSTGRES_DB=db \
  -p 5432:5432 postgres             | запуск PostgreSQL
- docker exec -it <container> psql -U user db | psql в контейнере
- docker logs <container>           | логи PostgreSQL
- docker volume ls                  | volume
- docker volume inspect <volume>    | данные БД

---

## ⚙️ Переменные окружения
- POSTGRES_USER                    | пользователь
- POSTGRES_PASSWORD                | пароль
- POSTGRES_DB                      | база данных
- PGHOST                            | хост
- PGPORT                            | порт
- PGUSER                            | пользователь
- PGPASSWORD                       | пароль
- PGDATABASE                        | база данных

---

## 🧰 Полезные команды psql
- \?                               | помощь
- \h                               | SQL help
- \timing                          | время выполнения
- \x                               | расширенный вывод
- \watch 2                         | автообновление
- \set ON_ERROR_STOP on            | стоп при ошибке

---

## 🚀 Best Practices (Dev)
- Используй миграции (Flyway, Liquibase)
- Храни пароли в .env
- Делай индексы для WHERE / JOIN
- Используй EXPLAIN ANALYZE
- Не используй SUPERUSER в проде
- Разделяй dev / stage / prod
- Делай регулярные бэкапы

---

## 📁 Типичные файлы
- docker-compose.yml
- .env
- init.sql
- migrations/
- schema.sql
- seed.sql

---