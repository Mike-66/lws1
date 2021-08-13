to set up project do:

composer install

cp .env.example  .env

php artisan key:generate

in .env adjust your database parameters and

    BROADCAST_DRIVER=pusher
    PUSHER_APP_ID=your_pusher_app_id
    PUSHER_APP_KEY=your_pusher_app_key
    PUSHER_APP_SECRET=your_pusher_app_secret

php artisan migrate

npm install

npm run watch

php artisan websockets:serve

