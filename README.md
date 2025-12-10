# ADS開発プロジェクト 運用マニュアル & テンプレート集

本リポジトリは、自動運転システム（ADS: Autonomous Driving System）開発プロジェクトにおける **Redmine/GitLab運用マニュアル** および **Wiki/READMEテンプレート** を集約したものです。

## 概要

本プロジェクトは、自動運転システムをアジャイルとVモデルのハイブリッドで開発します。
- **Redmine**: 要件管理・進捗管理
- **GitLab**: コード管理・設計書管理（Docs as Code）

## 対象読者

| 読者 | 参照すべきドキュメント |
|------|------------------------|
| Redmine管理者 | Section 1, Section 1.5 |
| 開発者・エンジニア | Section 2, Section 2.5, Section 3 |
| 新規参画者 | 全セクション（Section 2から開始推奨） |
| リポジトリ作成者 | Section 4 |

## ファイル構成

```
.
├── README.md                              # 本ファイル
├── CLAUDE.md                              # AI開発支援設定
├── .gitignore                             # Git除外設定
├── .dockerignore                          # Docker除外設定
│
├── docs/                                  # ドキュメント本体
│   ├── INDEX.md                           # ドキュメント目次・ナビゲーション
│   │
│   ├── redmine/                           # Redmine関連ドキュメント
│   │   ├── 01_admin_guide.md              # Section 1: 初期設定・管理者ガイド
│   │   ├── 01-5_custom_fields.md          # Section 1.5: カスタムフィールド定義
│   │   ├── 02_operation_rules.md          # Section 2: 運用ルール & Wikiテンプレート
│   │   └── 02-5_definition_of_done.md     # Section 2.5: 完了の定義 (DoD)
│   │
│   └── gitlab/                            # GitLab関連ドキュメント
│       └── 03_gitlab_guide.md             # Section 3: 初期設定・運用ガイド
│
└── templates/                             # テンプレート集
    ├── README_template.md                 # Section 4: リポジトリREADMEテンプレート
    ├── CONTRIBUTING.md                    # コントリビューションガイドテンプレート
    │
    └── diagrams/                          # 図表テンプレート
        └── ads_system_architecture.md     # ADSシステムアーキテクチャ図（Mermaid）
```

## 各セクションの内容

| セクション | ファイル | 内容 |
|------------|----------|------|
| Section 1 | [01_admin_guide.md](docs/redmine/01_admin_guide.md) | プロジェクト階層設定、トラッカー/ワークフロー、バージョン共有、カスタムクエリ |
| Section 1.5 | [01-5_custom_fields.md](docs/redmine/01-5_custom_fields.md) | ASILレベル、混入工程、根本原因、レビュー担当者のカスタムフィールド定義 |
| Section 2 | [02_operation_rules.md](docs/redmine/02_operation_rules.md) | 「迷ったら00_SystemDesign」ルール、トリアージ運用、Wikiテンプレート |
| Section 2.5 | [02-5_definition_of_done.md](docs/redmine/02-5_definition_of_done.md) | 実装タスク/バグ修正/成果物/ストーリー/エピックのDoDチェックリスト |
| Section 3 | [03_gitlab_guide.md](docs/gitlab/03_gitlab_guide.md) | リポジトリ構成、ディレクトリ構造、Docs as Code、ブランチ戦略、CI/CD設定 |
| Section 4 | [README_template.md](templates/README_template.md) | 各リポジトリ用README.mdテンプレート（モジュール別カスタマイズ例含む） |

## クイックスタート

### 1. Redmine管理者向け
```bash
# 以下の順序で設定を実施
docs/redmine/01_admin_guide.md      # プロジェクト・トラッカー設定
docs/redmine/01-5_custom_fields.md  # カスタムフィールド設定
```

### 2. 開発者向け
```bash
# 運用ルールを確認
docs/redmine/02_operation_rules.md
docs/redmine/02-5_definition_of_done.md

# GitLab運用を確認
docs/gitlab/03_gitlab_guide.md
```

### 3. 新規リポジトリ作成時
```bash
# テンプレートをコピーして使用
cp templates/README_template.md /path/to/new-repo/README.md
cp templates/CONTRIBUTING.md /path/to/new-repo/CONTRIBUTING.md
```

## Redmineプロジェクト階層

本マニュアルが対象とするRedmineプロジェクト構成：

```
ADS_Root (親プロジェクト)
├── 00_SystemDesign    # システム設計・アーキテクチャ・迷子タスク一時置き場
├── 01_Perception      # 認知モジュール（AI/カメラ）
├── 02_Planning        # 計画モジュール（経路計画）
├── 03_Embedded        # 組込みモジュール（ECU/センサー）
├── 04_QA              # 品質保証（テスト計画・シミュレーション）
└── 99_Library         # 資産管理（確定した仕様書・成果物）
```

## 関連リンク

- [ドキュメント目次](docs/INDEX.md)
- Redmine: `https://[your-redmine-url]/projects/ads_root`
- GitLab: `https://[your-gitlab-url]/ads`

## ライセンス

本ドキュメントは社内利用を目的としています。

---

**更新履歴**

| 日付 | 内容 |
|------|------|
| 2025-12-10 | 初版作成 |
