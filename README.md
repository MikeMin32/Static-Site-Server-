# Static-Site-Server-

## Setup a remote linux server on any cloud service provider 

Connect to this server using SSH:
```bash
ssh -i <path-to-private-key> user@server-ip
```
Install and configure nginx
```bash
sudo apt install nginx

sudo systemctl start nginx
sudo systemctl enable nginx
```

Make sure the server is running:
```bash
sudo systemctl status nginx
```

By default, Ubuntu's UFW firewall blocks most incoming connections. To allow traffic on port 80 (for HTTP) and port 443 (for HTTPS), execute the following:
```bash
sudo ufw allow 'Nginx Full'
```
## Deploy Your Static Website

Upload your static website files (HTML, CSS, JS) to the default web root directory:

```bash
sudo rm -rf /var/www/html/*
sudo cp -r <path-to-your-static-site>/* /var/www/html/
```

You can verify that your site is live by visiting:
```bash
http://<your-server-ip>
```

## (Optional) Configure a Custom Domain

If you own a domain, point its A record to your server's IP address.
Then update the Nginx configuration:

```bash
sudo nano /etc/nginx/sites-available/default
```
Replace the server_name line with:

server_name yourdomain.com www.yourdomain.com;

Restart Nginx to apply changes:

```bash
sudo systemctl restart nginx
```

## (Optional) Enable HTTPS with Let's Encrypt

Install Certbot:

```bash
sudo apt install certbot python3-certbot-nginx
```

Run Certbot to obtain and install the SSL certificate:

```
sudo certbot --nginx
```

Follow the prompts to complete the setup. Your site will now be available at:

https://yourdomain.com

## Done!

You’ve successfully deployed a static website using Nginx on a remote Linux server.

## Roadmap.sh project
Project URL: https://roadmap.sh/projects/static-site-server
