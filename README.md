# 1. Клонируйте репозиторий
git clone <your-repo-url>
cd <project-name>

# 2. Запустите Docker-контейнеры
docker-compose -f deploy/docker-compose.yml up -d --build

# 3. Выполните команды настройки Laravel внутри контейнера
docker-compose -f deploy/docker-compose.yml exec app bash
# (Внутри контейнера)
composer install
php artisan key:generate
php artisan migrate --seed
exit

# 4. Проверьте в браузере
# http://localhost/api/products
