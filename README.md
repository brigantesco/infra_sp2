REST API YamDB - база отзывов о фильмах, музыке и книгах

В директории infra создайте файл .env с переменными окружения для работы с базой данных:

DJANGO_KEY='your Django secret key'
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД

Как запустить проект:

Перейти в папку infra и запустить docker-compose.yaml (при установленном и запущенном Docker)

cd infra_sp2/infra
docker-compose up
Для пересборки контейнеров выполнять команду: (находясь в папке infra, при запущенном Docker)

docker-compose up -d --build
В контейнере web выполнить миграции:

docker-compose exec web python manage.py migrate
Создать суперпользователя:

docker-compose exec web python manage.py createsuperuser
Собрать статику:

docker-compose exec web python manage.py collectstatic --no-input
Проверьте работоспособность приложения, для этого перейдите на страницу:

 http://localhost/admin/
Документация (запросы для работа с API):

 http://localhost/redoc/