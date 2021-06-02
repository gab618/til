# Deploy Node server

<!-- Today I learned how to use ```jsonwebtoken``` for JWT authentication. -->

## 1. Criar server

- Criar novo droplet
  - Distribuição: Docker on Ubuntu (encontrar no marketplace)
- SSH
  - ssh-keygen (gerar chave se nao tem ainda)
  - copiar de ~/.ssh/id_rsa.pub
- Tudo padrão

---

## 2. Configuração inicial

- Terminal > ssh root@ip
- Atualizar > apt update && apt upgrade
- Criar novo usuário > adduser deploy
- Sudo > usermod -aG sudo deploy
- Autorizar ssh pro user deploy
  - mkdir .ssh em /home/deploy
  - cp ~/.ssh/authorized_keys /home/deploy/.ssh
  - chown deploy:deploy authorized_keys
- Instalar Node e npm
  - [Node.js binart distributions](https://github.com/nodesource/distributions/blob/master/README.md)
    -Sessão ssh longa
  - sudo vim /etc/ssh/ssh_config
  - ```
    ClientAliveInterval 30
    TCPKeepAlive yes
    ClientAliveCountMax 99999
    ```

```
___
## 3. Clonando o projeto

- git clone https://github.com/gab618/bolao-cblol.git app
- cd app && npm install
- .env

___
## 4. Serviços

- docker
  - Post-installation > sudo usermod -aG docker $USER && exit
  - Install postgres: docker run --name postgres -e POSTGRES_PASSWORD=docker123 -p 5432:5432 -d -t postgres
  - Create or import new database (usar postbird é mais facil)
  - npx sequelize db:migrate

## 5. Rodando o server
  - npm run build && npm run start
  - sudo ufw allow 3333 //para testar

```

## 5. Dominio

- Add dominio no digitalocean
- Add nameservers no dominio
- Instalar nginx > sudo apt install nginx
- Criar config do server

```
sudo nano /etc/nginx/sites-available/bolaocblol.tk.conf
```

```
server {
  listen 80;

  server_name bolaocblol.tk www.bolaocblol.tk;

  location / {
    proxy_pass http://localhost:3333; # Change the port if needed
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
  }
}
```

- Alguma coisa de symlink (?)

```
sudo ln -s /etc/nginx/sites-available/bolaocblol.tk.conf /etc/nginx/sites-enabled/
```

```
sudo service nginx restart
```

- Certbot

```
#Installation
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:certbot/certbot
sudo apt update
sudo apt install python3-certbot-nginx

#Getting the certificate
sudo certbot --nginx
```

```
sudo service nginx restart
```

## 6. PM2

- Instalar pm2

```
sudo npm install -g pm2
```

- Add o server

```
pm2 start dist/server.js
```

- Startup

```
pm2 startup systemd
# executar a resposta
```

- comandos
  - pm2 list
  - pm2 monit
