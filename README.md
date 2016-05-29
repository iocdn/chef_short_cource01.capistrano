# [初級]運用自動化ツールChef capistranoのサンプル

## 概要

リモートノードに対してchefを実行するサンプル     
リモートノードは左記のように設定する chef-repo/node/環境名/ノード名.json

# 本サンプルの使い方
本サンプルのコマンドは chef-repoディレクトリ直下で実行してください。

## capistranoのインストールと初期設定
- capistranoのインストール

```
$ chef exec gem install capistrano
```

- gitのインストール

```
$ yum -y install git
```

- capistrano基本ファイルの生成

```
$ cd ~/chef-repo
$ chef exec cap install
 automation features?  (Yes/no): no  <== 自動更新no
```

- 本サンプルの配置
```
 $ wget https://raw.githubusercontent.com/iocdn/chef_short_cource01.capistrano/master/config/deploy.rb  -O config/deploy.rb
```

- 環境変数ファイルの作成
```
$ touch config/deploy/development.rb
```
## リモートノードの登録
- リモートノード情報の作成
```
$ knife node create node1

{
  "name": "node1",
  "server": "リモートノードのIPアドレス",
  "chef_environment": "development",
  "default": {},
  "override": {},
  "run_list": [
    "Apache"  // cookbook name
  ]
}
```
- ノード情報を nodes/developmentに格納
```
$ mkdir nodes/development
$ mv nodes/node1.json nodes/development
```

# リモートノードに対してchefの実行
```
chef exec cap chef:all
```

# おまけ
- ノード一覧の取得
```
$chef exec cap development list_server
```

- ノードのuptime,freeメモリの確認
```
$ chef exec cap development uptime
$ chef exec cap development mem
```
- ノードに対して一括でコマンド実行
```
$ chef exec cap development console
```

- ruby の書式チェック(超簡易版)
```
$ chef exec cap development ruby_c
```
