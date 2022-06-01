# Next.js Laravel Docker

## 環境構築

``` sh
cd LAMP

docker compose up -d

# Laravel コンテナ ssh

docker exec -it lamp-apache bash

# mysql コンテナ ssh
docker exec -it lamp-mysql bash

# Next.js コンテナ ssh
docker exec -it lamp-nextjs sh

```

## Laravel 環境初期構築

``` sh
composer create-project --prefer-dist laravel/laravel プロジェクト名 "バージョン指定"
```

## Next.js 環境処置構築

``` sh
npx create-next-app
touch tsconfig.json
npm install --save-dev typescript @types/react @types/node
npm install sass
```

## アクセス

1. Laravel
   - http://localhost:8080
2. Next.js
   - http://localhost:3000
