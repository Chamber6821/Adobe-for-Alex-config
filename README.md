![image](https://github.com/user-attachments/assets/fb3ec452-65e1-43cd-b0f2-5398962be21d)# Запросы отправляемые между сервисами

![image](https://github.com/user-attachments/assets/77a15ddf-8044-45ec-bef3-4dbb38073435)

# Структура `.env` файла

## Пример

```sh
DATABASE_USER=testuser
DATABASE_PASSWORD=testpassword
TELEGRAM_BOT_TOKEN_SOFTPLUS=XXXXXX
TELEGRAM_BOT_TOKEN_CHEAPPY=XXXXXX
TELEGRAM_BOT_TOKEN_QUICK_SOLUTION=XXXXXX
TELEGRAM_BOT_TOKEN_ADOBE_SYSTEM=XXXXXX
PROXY_LIST_URL="https://asocks-list.org/mltLvve3TtOFUCz7FE64s9kjDnQdYzBJ.json?limit=10&type=corp"
```

## `DATABASE_USER` и `DATABASE_PASSWORD`

Имя пользователя и егг пароль от имени которого будут выполняться операции в БД.
Изменив файл `docker-compose.yml` можно настроить для каждого сервиса отдельногог пользователя

## `TELEGRA_BOT_TOKEN_*`

Токен для управления конкретным Telegram ботом. Можно получить от @BotFather в Telegram

## `PROXY_LIST_URL`

Ссылка на список доступных прокси серверов от сервиса [Asocks](https://my.asocks.com). На GET запрос должен возвращаться JSON масси следующего формата

```json
[
  "93.190.142.109:15244",
  "93.190.141.73:26460",
  "89.39.107.139:13629",
  "175.110.113.241:26265",
  "92.204.241.167:29740"
]
```

Хотя бы 1 сервер должен поддерживать HTTP прокси. Asocks отдает вперемешку список рабочи и нерабочих прокси серверов, поэтому в сервисе выбирается любой рабочий прокси сервер из полученного списка по этому запросу
