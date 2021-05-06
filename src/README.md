## 開発 Dock

## 採用技術

-   php8
-   Laravel6
-   php-cs-fixer

## 設計

### 構造

-   異論がありそうですが、ゆるい clean architecture にしました
    -   厳密に守ると Laravel の機能が損なわれるため
    -   コードの煩雑さが生産性に見合わないため
-   https://github.com/ibrunotome/laravel-api-templates/tree/master/default-structure
-   https://zenn.dev/mpyw/articles/ce7d09eb6d8117

```bash
.
├── .editorconfig
├── .env
├── .env.example
├── .gitattributes
├── .gitignore
├── .php_cs.cache
├── .php_cs.dist
├── .styleci.yml
├── webpack.mix.js
├── README.md
├── artisan
├── composer.json
├── composer.lock
├── package.json
├── phpunit.xml
├── server.php
├── app
│   ├── Console
│   ├── Domains
│   ├── Exceptions
│   ├── Http
│   │   ├── Controllers
│   │   │   ├── Auth
│   │   │   └── Controller.php
│   │   ├── Kernel.php
│   │   ├── Middleware
│   │   ├── Requests
│   │   └── Resorces
│   ├── Models
│   ├── Providers # 今回使わないはず
│   ├── Usecases # ビジネスロジックはここに
│   └── User.php
├── bootstrap # 特にいじってない
├── config
│   ├── app.php
│   ├── auth.php
│   ├── broadcasting.php
│   ├── cache.php
│   ├── database.php
│   ├── filesystems.php
│   ├── hashing.php
│   ├── logging.php
│   ├── mail.php
│   ├── queue.php
│   ├── services.php
│   ├── session.php
│   └── view.php
├── database
│   ├── factories
│   │   └── UserFactory.php
│   ├── migrations
│   │   ├── ddl # 初期のDB定義
│   │   └── mods # DBに対し変更等かける際に動くsql
│   └── seeds
│       └── DatabaseSeeder.php
├── docks # apiの定義書
├── public # 使っていないはず
├── resources # 使っていないはず
├── routes
│   ├── api.php
│   ├── channels.php
│   ├── console.php
│   └── web.php # 使っていないはず
├── storage # 今回使いません
└── tests
    ├── CreatesApplication.php
    ├── Feature # 結合テスト
    ├── TestCase.php
    └── Unit # 単体テスト

```

## 開発ルール

### DB 方針

-   DB は直接触らず、必ず migration file を利用すること
-   テーブルを追加修正した場合、ER 図も忘れずに更新すること

### テスト方針

-   ユニットテストは必ず書くこと
-   API を作成・修正した場合、必ず open api 定義を更新すること

### 開發の流れ

-   develop ブランチからブランチを切る（ブランチ名は、`feature/{backlogの番号}`にすること）
-   実装と単体テスト作成を終えたら、PR を develop 向けに出す
-   PR を作成したことをチャットでレビュー担当者に通知
-   マージされたら終了！
