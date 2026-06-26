## pip install gunicorn

## Test: 
gunicorn config.wsgi:application

## create systemmd service
sudo nano /etc/systemd/system/app.service

# Add #
[Unit]
Description=CApp Django Application
After=network.target

[Service]
User=ubuntu
Group=www-data

WorkingDirectory=/home/ubuntu/Documents/projects/app/backend

Environment="PATH=/home/ubuntu/Documents/projects/app/venv/bin"

ExecStart=/home/ubuntu/Documents/projects/app/venv/bin/gunicorn \
          --workers 3 \
          --bind 0.0.0.0:8000 \
          config.wsgi:application

Restart=always

[Install]
WantedBy=multi-user.target

## Start
sudo systemctl daemon-reload

sudo systemctl enable app

sudo systemctl start app


