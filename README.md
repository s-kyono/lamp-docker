# LAMP (ApacheのところをNginxに変えてます...)

## 前提

- git clone で本リポジトリをcloneできていること
- ホストマシンに dockerがインストールされていること

1. 構成

``` sh
    api-server
        ├── バックエンドプロジェクト ※Laravel想定
    docker
        ├── php
            └── phpを構成するdocker,config ファイル
        ├── nginx
            └── nginxを構成するdocker,config ファイル
        ├── mysql
            └── mysqlを構成するdocker,config ファイル
        ├── docker-compose.yml docker起動ファイル
    front-server
        └──  フロントエンドプロジェクト ※Next.js想定
```

2. 環境構築

- SSL証明書を作成
  - 以下のSSL証明書作成ツールを用いていおります
  - [open-ssl](https://www.openssl.org/)
    - windows mac opensslのインストール方法が異なります
  - [mkcert](https://github.com/FiloSottile/mkcert)

- 起動

``` sh
cd docker
docker-compose up -d
```

``` sh
# いかが出力されていればOK
✔ Network docker_default  Created
✔ Container lamp-mysql    Started
✔ Container lamp-php      Started
✔ Container lamp-nginx    Started
```

- api-serverにLaravelプロジェクトを作成 ※作祭されていない場合

- ホストマシンにドメイン登録

- mac

``` ssh
sudo vi /etc/hosts
```

- windows
  - powershellにて追記
  - 以下コマンドを実行しメモ帳が開くため

``` ssh
powershell -NoProfile -ExecutionPolicy unrestricted -Command "start notepad C:\Windows\System32\drivers\etc\hosts -verb runas"
```

``` text
# 以下を追記

127.0.0.1 lamp.local.example-dev.com
127.0.0.1 lamp.local.mkcert.example-dev.com

```

- 以下でアクセスできることを確認 (バックエンドURL)
  - https://lamp.local.example-dev.com:4000
  - https://lamp.local.example-dev.com:4430
  - https://lamp.local.mkcert.example-dev.com:4430
  - https://lamp.local.mkcert.example-dev.com:4430
