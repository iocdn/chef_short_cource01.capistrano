# [初級]運用自動化ツールChef capistranoのサンプル

## 概要

リモートノードに対してchefを実行するサンプル     
リモートノードは左記のように設定する chef-repo/node/環境名/ノード名.json

# 本サンプルの使い方
## capistranoのインストールと初期設定
- インストール

```
$ chef exec gem install capistrano
```

- capistrano基本ファイルの生成

```
$ chef exec cap install
 automation features?  (Yes/no): no  <== 自動更新no
```

- 環境変数ファイルの作成
```
$ touch config/deploy/development.rb
```
## リモートノードの登録手順
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
