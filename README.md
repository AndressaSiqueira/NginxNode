# NginxNode

Instalar node e nginx (https://docs.oracle.com/en/learn/oracle-linux-nginx/) na máquina

NODE

Colocar app .js em /var/www/qualquercoisa.com
App tem que estar expondo localhost na porta 3000 por exemplo

NGINX:

Criar arquivo my.config em /etc/nginx/sites-avaliable
CONTEUDO:

server {
    listen 80;  # Substitua <IP> pelo endereço IP do seu servidor

    location / {
        proxy_pass http://localhost:3000;  # Encaminha as solicitações para a aplicação Node.js
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}

