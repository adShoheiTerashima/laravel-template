## 開発 Dock

## 採用技術

-   php8
-   Laravel6
-   php-cs-fixer
-   mysql8

## 設計

### 構造

-   異論がありそうですが、ゆるい clean architecture にしました
    -   厳密に守ると Laravel の機能が損なわれるため
    -   コードの煩雑さが生産性に見合わないため
    -   参考: https://zenn.dev/mpyw/articles/ce7d09eb6d8117
-   主な役割としては、以下となります
    -   Http/Controllers
        -   入出力のチェックと Usecase への受け渡し
        -   Http/Requests で入力のデータ定義とバリデーションルール定義
        -   Http/Resorces で出力時のデータを管理
    -   Usecases
        -   ビジネスロジックを実行する、メインの処理
    -   Models
        -   DB とのやりとりを管理

## 開発ルール

### コーディングルール

-   基本的には、lint の通り
-   **型は必ずつけること**
-   その他、実装しながら随時話し合っていければと！

### DB 方針

-   定義変更する際は、DB は直接触らず必ず migration file を利用すること
-   テーブルを追加修正した場合、ER 図も忘れずに更新すること
-   新規にテーブルを作成した場合、created_at と updated_at は必ず作ること
-   中間テーブルの命名規則は以下のとおり（ソースが Qiita ですみません）
    -   https://qiita.com/tkawa/items/dc3e313021f32fd91ca6
-   カラム名の命名規則
-   〜flg 禁止（２択なら、isXXX で表せるはず）
-   AUTO INCREMENT、created_at、updated_at 以外のカラムにはコメント書きましょう

### テスト方針

-   ユニットテストは必ず書くこと
-   ユニットテストを書く対象は、`Usecases`下ファイルと、`Http/Requests`下ファイルで十分かな？要相談
-   テストの粒度は、c1（分岐網羅）でお願いします

### 開發の流れ

-   develop ブランチからブランチを切る（ブランチ名は、`feature/backlog-{backlogの番号}`もしくは`feature/issue-{issue番号}`にすること）
-   実装と単体テスト作成を終えたら、PR を develop 向けに出す
-   PR を作成したことをチャットでレビュー担当者に通知
-   マージされたら終了！マージされたらブランチは消していきましょう
