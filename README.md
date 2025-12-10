ファイル構成

```
  docs/
  ├── INDEX.md                          # ドキュメント目次
  ├── redmine/
  │   ├── 01_admin_guide.md              # Section 1: Redmine 初期設定・管理者ガイド
  │   ├── 01-5_custom_fields.md          # Section 1.5: カスタムフィールド定義
  │   ├── 02_operation_rules.md          # Section 2: 運用ルール & Wikiテンプレート
  │   └── 02-5_definition_of_done.md     # Section 2.5: 完了の定義 (DoD)
  ├── gitlab/
  │   └── 03_gitlab_guide.md             # Section 3: GitLab 初期設定・運用ガイド
  templates/
      ├── diagrams
      │   └── ads_system_architecture.md # Section 4: Mermaid Diagramテンプレート
      ├── CONTRIBUTING.md                # Section 4: README.mdテンプレート 追加ファイル
      └── README_template.md             # Section 4: README.mdテンプレート
  .gitignore                             # Git除外設定
  .dockerignore                          # Docker除外設定
```

  各セクションの内容

  | セクション       | 内容                                           |
  |-------------|----------------------------------------------|
  | Section 1   | プロジェクト階層設定、トラッカー/ワークフロー、バージョン共有、カスタムクエリ      |
  | Section 1.5 | ASILレベル、混入工程、根本原因、レビュー担当者のカスタムフィールド定義        |
  | Section 2   | 「迷ったら00_SystemDesign」ルール、トリアージ運用、Wikiテンプレート  |
  | Section 2.5 | 実装タスク/バグ修正/成果物/ストーリー/エピックのDoDチェックリスト         |
  | Section 3   | リポジトリ構成、ディレクトリ構造、Docs as Code、ブランチ戦略、CI/CD設定 |
  | Section 4   | 各リポジトリ用README.mdテンプレート（モジュール別カスタマイズ例含む）      |
