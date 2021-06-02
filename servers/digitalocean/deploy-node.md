# Deploy Node server

<!-- Today I learned how to use ```jsonwebtoken``` for JWT authentication. -->

## 1.Criar server

- Criar novo droplet
  - Distribuição: Docker on Ubuntu (encontrar no marketplace)
- SSH
  - ssh-keygen (gerar chave se nao tem ainda)
  - copiar de ~/.ssh/id_rsa.pub
- Tudo padrão

## 2.Configuração inicial

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
