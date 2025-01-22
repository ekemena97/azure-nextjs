## Deploy Nextjs App to Azure

installing nodejs

```
cd ~
curl -sL https://deb.nodesource.com/setup_20.x -o nodesource_setup.sh
sudo bash nodesource_setup.sh
sudo apt install nodejs


```

Installing npm

```
sudo apt install npm
```

clone the app
```
git clone your-repo
```

Install packages
```
npm install
```

Install pm2
```
npm install -g pm2

```


Build nextjs
```
npm run build
```

Start nextjs
```
pm2 start npm --name "nextjs-app" -- run start

```

Check status
```
pm2 list

```

Log the nextjs app
```
pm2 logs nextjs-app
```


Install Nginx
```
    
npm install nginx
```

Nginx Configuration


```
sudo vi sudo nano /etc/nginx/sites-available/nextjs

server {
    listen 80;
    server_name example.com;  # Replace with your domain or IP address

    location / {
        proxy_pass http://localhost:3000;  # Forward requests to the Next.js app
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}

```

Check if Nginx config is correct

```
nginx -t
```

Enable the configuration
```
sudo ln -s /etc/nginx/sites-available/nextjs /etc/nginx/sites-enabled/

```