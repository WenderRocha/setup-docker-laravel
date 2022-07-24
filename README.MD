# Setup Docker Para Projetos Laravel (8 ou 9)
Compativel tambem com projetos laravel/breeze porem ainda não é possivel utilizar o comando npm run dev. funciona normalmente após npm run build.

### Passo a passo
Clone Repositório
```sh
git clone https://github.com/WenderRocha/setup-docker-laravel.git
```

Clone os Arquivos do Laravel
```sh
git clone https://github.com/laravel/laravel.git app-laravel
```


Copie os arquivos docker-compose.yaml, Dockerfile e o diretório docker/ para o seu projeto
```sh
cp -rf setup-docker-laravel/* app-laravel/
```
```sh
cd app-laravel/
```

Edite o arquivo docker-compose.yaml
acesse o service app em args altere o nome do user para o seu usuário.
```sh
user: seu usuario
```

Crie o Arquivo .env
```sh
cp .env.example .env
```


Atualize as variáveis de ambiente do arquivo .env
```dosini
APP_NAME=EspecializaTi
APP_URL=http://localhost:8989

DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=nome_que_desejar_db
DB_USERNAME=nome_usuario
DB_PASSWORD=senha_aqui

CACHE_DRIVER=redis
QUEUE_CONNECTION=redis
SESSION_DRIVER=redis

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379
```


Suba os containers do projeto
```sh
docker-compose up -d
```


Acessar o container
```sh
docker-compose exec app bash
```


Instalar as dependências do projeto
```sh
composer install
```

Gerar a key do projeto Laravel
```sh
php artisan key:generate
```

Acessar o projeto
[http://localhost:8989](http://localhost:8989)