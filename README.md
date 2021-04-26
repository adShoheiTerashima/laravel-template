# Laravel 用テンプレート

## 概要

### 目的

- 1 から環境構築する手間を省くため
- プロジェクトメンバーやエンジニアの力量による品質差を少なくするため

### ディレクトリ説明

```bash
root
├── .github
│ └── workflows   # output
├── docker        # docker-compose.yml等、実行環境周り
│ └── openapi   # open apiの実行環境。swagger editorとかmockサーバとか
├── src           # 詳しくはsrc/README.md参照
└── README.md     # me!
```

### 注意

- 細かい開発ルールは src/README.md を参照してください

---

## 環境構築

### 開発環境の立て方

1. docker/app ディレクトリに移動する
1. `docker-compose up -d`する
1.

### API mock サーバの立ち上げ方

1. docker/openapi ディレクトリに移動する
1. `docker-compose up -d`する
1. port がかぶっていなければ、`localhost:19883`を叩けばいけるはず

### API editor & API UI

1. docker/openapi ディレクトリに移動する
1. `docker-compose up -d`する
1. editor は`localhost:19881`、ui は`localhost:19882`を叩く
