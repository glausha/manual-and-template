# ADS開発プロジェクト ドキュメントインデックス

自動運転システム（ADS）開発プロジェクトにおける Redmine/GitLab 運用マニュアルおよびテンプレート集。

---

## ドキュメント構成

```
docs/
├── INDEX.md                          # 本ファイル（目次）
├── redmine/                          # Redmine関連ドキュメント
│   ├── 01_admin_guide.md            # Section 1: 管理者ガイド
│   ├── 01-5_custom_fields.md        # Section 1.5: カスタムフィールド定義
│   ├── 02_operation_rules.md        # Section 2: 運用ルール & Wikiテンプレート
│   └── 02-5_definition_of_done.md   # Section 2.5: 完了の定義 (DoD)
├── gitlab/                           # GitLab関連ドキュメント
│   └── 03_gitlab_guide.md           # Section 3: GitLab運用ガイド
templates/
└── README_template.md                # Section 4: README.mdテンプレート
```

---

## 目次

### Redmine関連

| セクション | ドキュメント | 対象読者 | 概要 |
|-----------|-------------|----------|------|
| **Section 1** | [Redmine 初期設定・管理者ガイド](redmine/01_admin_guide.md) | 管理者 | プロジェクト階層、トラッカー、ワークフロー、バージョン共有設定 |
| **Section 1.5** | [カスタムフィールド定義](redmine/01-5_custom_fields.md) | 管理者 | ASILレベル、混入工程、根本原因、レビュー担当者フィールドの定義 |
| **Section 2** | [運用ルール & Wikiテンプレート](redmine/02_operation_rules.md) | 開発者/管理者 | チケット起票ルール、トリアージ運用、Wikiテンプレート |
| **Section 2.5** | [完了の定義 (DoD)](redmine/02-5_definition_of_done.md) | 開発者/QA | 実装タスク、バグ修正、成果物のDoDチェックリスト |

### GitLab関連

| セクション | ドキュメント | 対象読者 | 概要 |
|-----------|-------------|----------|------|
| **Section 3** | [GitLab 初期設定・運用ガイド](gitlab/03_gitlab_guide.md) | 開発者/管理者 | リポジトリ構成、ディレクトリ構造、Docs as Code、ブランチ戦略 |
| **Section 4** | [README.md テンプレート](../templates/README_template.md) | 開発者 | 各リポジトリ用README.mdのテンプレート |

---

## クイックスタート

### 新規プロジェクト立ち上げ時

1. **Redmine管理者**
   - [Section 1](redmine/01_admin_guide.md) に従いプロジェクト階層を作成
   - [Section 1.5](redmine/01-5_custom_fields.md) に従いカスタムフィールドを設定
   - Wikiテンプレート（[Section 2](redmine/02_operation_rules.md)）を各プロジェクトに展開

2. **GitLab管理者**
   - [Section 3](gitlab/03_gitlab_guide.md) に従いリポジトリを作成
   - [Section 4](../templates/README_template.md) のテンプレートでREADME.mdを作成
   - CI/CDパイプラインを設定

### 開発者オンボーディング時

1. [Section 2: 運用ルール](redmine/02_operation_rules.md) を一読
2. [Section 2.5: 完了の定義](redmine/02-5_definition_of_done.md) を確認
3. [Section 3: GitLab運用ガイド](gitlab/03_gitlab_guide.md) のブランチ戦略を理解

---

## 更新履歴

| 日付 | バージョン | 変更者 | 変更内容 |
|------|-----------|--------|----------|
| YYYY-MM-DD | v1.0.0 | [名前] | 初版作成 |

---

## フィードバック

本ドキュメントに関するフィードバックは、Redmine `00_SystemDesign` プロジェクトに【ドキュメント改善】タグ付きでチケットを起票すること。
