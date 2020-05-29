# Dockerized IMI Component Tools
## 概要
経済産業省がMITライセンスで公開している[IMIコンポーネントツール](https://info.gbiz.go.jp/tools/imi_tools/)を Docker Image として扱いやすくするためのリポジトリです。WebUI が実装されている各ツールについて、Docker Compose で簡単に起動できるようにしてあります。

## 詳細
IMIコンポーネントツールのうち、WebUI が実装されている6つのツールについて、Dockerに載せています。具体的には、以下のコンポーネントを対象としています。

- 住所変換コンポーネント
- 法人種別名の抽出コンポーネント
- データバリデーションコンポーネント
- 電話番号正規化パッケージ一式
- 日付型正規化パッケージ一式
- 産業分類候補生成パッケージ一式

利用ポートは上から順に8080〜8085を割り当てています。お使いの環境に合わせて `docker-compose.yml` を編集し、空いているポートをお使いください。

## 起動方法
まず、各 Docker Image をビルドします。ビルドが終わったら起動してください。

```bash
$ docker-compose build
$ docker-compose up -d
```

6つあるうちのひとつだけ試したいときなど、個別の起動にも対応しています。以下のように、`docker-compose.yml` の `services` で定義されているコンポーネントの名称を入力してください。

```bash
$ docker-compose up -d enrichment-address
```

止めたいときは以下のようにしてください。コンテナごと削除されます。

```bash
$ docker-compose down -v
```

## ライセンス
MITとします。
