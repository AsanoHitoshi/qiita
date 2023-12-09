---
title: CentOS7にDocker、Docker Composeをインストールしよう
tags:
  - Docker
  - centos7
  - docker-compose
private: false
updated_at: '2020-05-10T00:37:11+09:00'
id: 87b6fb498cb3aa84bfff
organization_url_name: null
slide: false
ignorePublish: false
---
#Dockerをインストール
CentOSに今回は無償版のDocker（Docker CE）を導入する方法を説明します
##yumリポジトリ設定
まず、Dockerをインストールするための前準備として、下記のコマンドで必要なパッケージをインストールしましょう
下記のコマンドでインストールされるパッケージは`yum-utils`、`device-mapper-persistent-data`、`lvm2`の3つです

```:ターミナル
yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
```

次にyumリポジトリを設定します。
下記のコマンドで`docker-ce.repo`というリポジトリを追加します

```:ターミナル
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

上記のコマンドで`docker-ce.repo`が作成されているか確認しましょう
下記のコマンドで`/etc/yum.repos.d/`内に`docker-ce.repo`が作成されていることを確認しましょう

```:ターミナル
ll /etc/yum.repos.d/
```

以上でDockerをインストールする準備は完了です

##Dockerのインストール
次にDocker CEをインストールします
下記のコマンドを実行しましょう

```:ターミナル
yum install docker-ce
```

##インストールの確認
次にインストールができているか確認しましょう

```:ターミナル
# yum list installed | grep docker-ce
docker-ce.x86_64 17.12.0.ce-1.el7.centos @docker-ce-stable
# docker -v
Docker version 18.03.1-ce, build 9ee9f40
```

実行結果が同じようになればDocker CEのインストールが完了です！！
時期によってバージョンの違いはあると思うので、気にしないでください

##Dockerサービスの操作方法
ついでにDockerサービスの操作方法についても記述します

```
//サービス起動
systemctl start docker

//サービス停止
systemctl stop docker

//サービスの再起動
sudo systemctl restart docker

//サービスの稼働状態の表示
systemctl status docker

//自動起動設定
systemctl enable docker
```

#Docker Composeのインストール
次にDocker Composeをインストールします
##Docker Composeのインストール
下記のコマンドでDocker Composeのインストールと`docker-compose`の権限変更をします

```:ターミナル
# curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
# chmod +x /usr/local/bin/docker-compose
```

##インストールの確認
下記のコマンドでDocker Composeがインストールできているか確認しましょう

```:ターミナル
# docker-compose --version
docker-compose version 1.21.2, build 1719ceb
```

上記のような実行結果になればDocker Composeのインストールが完了です！！
