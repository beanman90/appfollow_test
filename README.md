# appfollow_test
Тестовое задание для [AppFollow](https://appfollow.io) на python-разработчика. Распространяется по лицензии MIT

## Запуск
Необходим docker>=17.06 и docker-compose>=3.3
`docker-compose up` и доступен по `http://localhost`

## Демо
[*однако однажды оно станет чем-то другим](http://194.182.84.137/)

## mypy, flake8
Все питоновские сервисы содержат в себе в качестве дев-зависимостей mypy и wemake-python-styleguide (flake8). Для их 
запуска нужно сделать что-нибудь эдакое:

`mypy .`

`flake8`

Чтобы не засорять систему можно воспользоваться `pipenv install --dev` и `pipenv run mypy .` соответственно.
## Сервисы

### fetcher
Сервис, просматривающий базу на наличие новых запросов и обрабатывающий их. Парсит ответ от непубличного GooglePlay 
Store API, скачивает картинки-иконки блоков разрешений.

### api
Сервис, предоставляющий API для отправки в базу запроса и отдачу полученных результатов. Содержит один грустный 
эндпоинт.

### frontend
Мини-фронтенд на vue + semantic-ui. Делает запросы, крутит лоадингом, выводит разрешения. Раздаётся nginx'ом вместе с
 картинками блоков разрешений. Собирается в момент сборки докерфайла через docker multi-stage build

## TODO:
 - [ ] Фатальный недостаток в fetcher модуле, на который аж линтер ругается -- слишком сложный парсинг блоков разрешений
 - [x] Демо
 - [ ] Не получилось использовать collection.watch, из того что понял -- нужно запустить монго в режиме репликации, 
 если будет скучно, надо будет побороть
 - [ ] Не запаривался с фронтендом, возможно стоит нормально разнести по компонентам и прибраться в стилях
