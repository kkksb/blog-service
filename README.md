# blog-service

個人用のブログサービス
dockerで自前の環境を汚さずにHaskellの学習ができるサンドボックスも兼ねている

## サンドボックスとしての使い方

### 必要な環境

Docker

### 推奨する環境

VSCode
  - Remote - Containers拡張
  - Haskell 拡張

Haskellの開発に必要・推奨なものはコンテナ内に展開するようにしたので

### コンテナの立ち上げ方

1. sandbox ブランチをチェックアウトする
2. /docker ディレクトリ内で docker compose up -d
3. VSCodeの Remote - Containersでコンテナ内に入る

### Haskellプロジェクトの立ち上げ方

1. コンテナ内の /opt/src に移動
2. stack new <プロジェクト名>
3. cd <プロジェクト名>
4. stack build
5. gen-hie > hie.yaml

これでVSCodeでHaskellがコード補完等込みで開発できる…はず
docker compose up, stack build には初回は尋常じゃない時間がかかるので気長に待ってね☆
