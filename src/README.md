## 採用技術

-   php8
-   Laravel6
-   php-cs-fixer

## 設計方針

-   異論がありそうですが、ゆるい clean architecture にしました
    -   厳密に守ると Laravel の機能が損なわれるため
    -   コードの煩雑さが生産性に見合わないため
-   https://github.com/ibrunotome/laravel-api-templates/tree/master/default-structure
-   https://zenn.dev/mpyw/articles/ce7d09eb6d8117

## 構造

```bash
app/
├── Console
├── Domains        # Domain model(entity)
├── Exceptions
├── Http
│ ├── Controllers  # controller
│ ├── Middleware
│ ├── Requests     # input
│ └── Resorces     # output
├── Models         # repository
├── Providers
└── Usecases       # usecase
```
