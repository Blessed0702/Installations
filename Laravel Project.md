## composer install

## Create environment:

cp .env.example .env

## php artisan key:generate

## php artisan migrate

## Windows
php artisan serve

## Linux 

## NGINX ##

sudo nano /etc/nginx/sites-available/crm-laravel

## ADD

server {

    listen 80;

    server_name laravel.example.com;


    root /home/ubuntu/Documents/projects/app/public;


    index index.php index.html;


    location / {

        try_files $uri $uri/ /index.php?$query_string;

    }


    location ~ \.php$ {

        include snippets/fastcgi-php.conf;

        fastcgi_pass unix:/run/php/php8.X-fpm.sock;  ## Run ls /run/php/ to check

    }


    location ~ /\.ht {

        deny all;

    }

}

## Enable:

sudo ln -s /etc/nginx/sites-available/crm-laravel /etc/nginx/sites-enabled/

## Test:

sudo nginx -t

## Restart:

sudo systemctl restart nginx

## Fix Laravel storage permissions:

sudo chown -R ubuntu:www-data /home/ubuntu/Documents/projects/Sales-Inventory-Management-System/storage

sudo chown -R ubuntu:www-data /home/ubuntu/Documents/projects/Sales-Inventory-Management-System/bootstrap/cache

sudo chmod -R 775 /home/ubuntu/Documents/projects/Sales-Inventory-Management-System/storage

sudo chmod -R 775 /home/ubuntu/Documents/projects/Sales-Inventory-Management-System/bootstrap/cache

## Linux requires execute (x) permission on every parent folder:

sudo chmod 755 /home/ubuntu
sudo chmod 755 /home/ubuntu/Documents
sudo chmod 755 /home/ubuntu/Documents/projects
sudo chmod 755 /home/ubuntu/Documents/projects/Sales-Inventory-Management-System
sudo chmod 755 /home/ubuntu/Documents/projects/Sales-Inventory-Management-System/public
