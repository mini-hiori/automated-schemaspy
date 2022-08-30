## automated-schemaspy

### 概要

- [SchemaSpy](https://schemaspy.org/)をGithub Actionsで定期実行し、常に最新のテーブル定義表を得られるようにする仕組み

### 使い方

- このリポジトリをforkしてください
- Github ActionsのSecretsとして、以下を作成してください
    - DB_HOST     : テーブル定義を取得したいDBのホスト(URL)
    - DB_NAME     : テーブル定義を取得したいDBのデータベース名
    - DB_SCHEMA   : テーブル定義を取得したいDBのスキーマ名
    - DB_USER     : テーブル定義を取得したいDBにログインするためのユーザー名
    - DB_PASSWORD : テーブル定義を取得したいDBにログインするためのパスワード
- Secretsを作成すると、毎日0時にSchemaSpyが起動してテーブル定義表が更新されます
    - リポジトリに `build/output/index.html` が作成されます。cloneしてローカルで開くとテーブル定義表を閲覧することができます

### 備考

- テーブル定義表にコメントを追加したい場合は、`schema-meta.xml` に追記した状態でGithub Actionsを再起動してください
- 生成物の `output` フォルダ以下全ファイルを移動すると、テーブル定義表の外部公開が可能です
    - 例: AWS S3に `output` フォルダ以下を配置し、[静的サイトホスティング](https://docs.aws.amazon.com/ja_jp/AmazonS3/latest/userguide/WebsiteHosting.html)機能を使って公開する
    - [Github Pages](https://docs.github.com/ja/pages/getting-started-with-github-pages/creating-a-github-pages-site)などでもできそう
- より詳しい説明は以下記事参照(内容は同じ)
    - [note]()
    - [Zenn]()