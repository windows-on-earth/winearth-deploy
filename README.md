# winearth-deploy

## Produdction Deployment

### Make directories for the SSL Certificates

    mkdir -p certbot/conf
    mkdir -p certbot/www
    mkdir -p log

### Generate Intial SSL Certificates

    docker run --name certbot -p 80:80 -v "$(pwd)/certbot/conf:/etc/letsencrypt" -v "$(pwd)/certbot/www:/var/www/certbot" certbot/certbot certonly --standalone --email <email> -d <hostname> --rsa-key-size 4096 --agree-tos --no-eff-email --non-interactive

### Deploy or Update the Stack

    docker compose up -d

### Delete the Stack

    docker compose down

## Development Deployment

### Overwrite the Production Nginx Conf File with the Development Nginx Conf File

    mv nginx/sites-enabled/winearth.conf-dev nginx/sites-enabled/winearth.conf

### Update docker-compose.yml with Local Development Docker Container Images (optional)

### Deploy or Update the Stack

    docker compose up -d

### Delete the Stack

    docker compose down