# Template Dashboard Admin Laravel 12 + Vue + Inertia.js

## Instalação

### Clonar o repositório
```
https://github.com/felipeemen/laravel-dashboard-vue
```
### Instalar Dependências
```
composer install
```

```
npm install
```

### Criar novo arquivo .env:
```
cp .env.example .env
```

### Gerar a chave da aplicação
```
php artisan key:generate
```

### Configurar banco de dados
Edite o arquivo ```.env``` com as credenciais do banco de dados.

### Rodar as migrations
```
php artisan migrate
```

### Compilar os assets
```
npm run dev
```
### Criar usuario
```
php artisan db:seed
```
```email: admin@localhost```

```password: admin```

### Rodar o servidor
```
php artisan serve
```
