# [初級]運用自動化ツールChef capistranoインストールと初期設定

## capistranoのインストール

```
$ chef exec gem install capistrano
```

## gitのインストール

```
$ sudo yum -y install git
```

## capistrano基本ファイルの生成

```
$ cd ~/chef-repo
$ chef exec cap install
 automation features?  (Yes/no): no  <== 自動更新no
```

## configファイルの配置
```
 $ wget https://raw.githubusercontent.com/iocdn/chef_short_cource01.capistrano/master/config/deploy.rb  -O config/deploy.rb
```

## 環境変数ファイルの作成
```
$ touch config/deploy/development.rb
```
