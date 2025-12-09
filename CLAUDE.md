ALWAYS use ONLY Environments for ANY and ALL file, code, or shell operations—NO EXCEPTIONS—even for simple or generic requests.

DO NOT install or use the git cli with the environment_run_cmd tool. All environment tools will handle git operations for you. Changing ".git" yourself will compromise the integrity of your environment.

You MUST inform the user how to view your work using `git checkout <branch_name>`. Failure to do this will make your work inaccessible to others.

Gitignoreファイル､Dockerignoreファイルを追加し､プライベートな設定がGithubにプッシュされないようにしてください｡
適切なSubAgentsを利用して以下に示すタスクを攻略してください。

---
```
# Role
あなたは大手自動車メーカーの自動運転開発プロジェクトにおける「開発プロセスコンサルタント」兼「テクニカルライター」です。
以下の要件に基づき、開発チームが参照するための**「Redmine/GitLab 運用マニュアル」**および**「Wiki/READMEテンプレート」**を作成してください。

# Context: プロジェクト構成
本プロジェクトは、自動運転システム（ADS）をアジャイルとVモデルのハイブリッドで開発します。
Redmineで要件・進捗管理を行い、GitLabでコード・設計書管理を行います。

## 1. Redmineプロジェクト階層
- **:package: ADS_Root (親)**: PMO管理、ロードマップ
- **:open_file_folder: 00_SystemDesign (システム設計)**: 技術仕様、アーキテクチャ、迷子タスクの一時置き場
- **:open_file_folder: 01_Perception (認知)**: AI/カメラ開発
- **:open_file_folder: 02_Planning (制御)**: 経路計画開発
- **:open_file_folder: 03_Embedded (組込)**: ECU/センサー
- **:open_file_folder: 04_QA (品質保証)**: テスト計画、シミュレーション
- **:open_file_folder: 99_Library (資産管理)**: 確定した仕様書・成果物の格納

## 2. トラッカー（チケット種別）
- エピック (Lv1) / ストーリー (Lv2) / タスク (Lv3) / バグ / 成果物 (Deliverable)

# Deliverables (出力成果物)
以下の4つのセクションに分けてMarkdown形式で出力してください。

---

## Section 1: Redmine 初期設定・管理者ガイド
Redmine管理者が設定すべき内容を箇条書きで整理してください。
1. **プロジェクト階層設定**: 上記Contextの階層構造と役割定義。
2. **トラッカーとワークフロー**:
   - エピック/ストーリー/タスクの親子関係ルール設定。
   - 「成果物」トラッカーの承認フロー（作成→レビュー→承認）。
3. **バージョン共有設定**: 親プロジェクト(ADS_Root)で作成したバージョンを「階層全体」に共有する設定手順。
4. **カスタムクエリ設定**: 「全プロジェクト横断・マイタスク」の作成方法。

## Section 1.5: Redmine カスタムフィールド定義
自動運転システム開発に必要な以下のカスタムフィールドの定義を追加してください。
それぞれのフィールドが「どのトラッカー」で「必須/任意」かも指定してください。

1. **ASILレベル (Safety Level)**: QM / A / B / C / D
   - 対象: エピック、ーストーリー
2. **混入工程 (Injection Phase)**: 要件定義 / 設計 / 実装 / テスト
   - 対象: バグ
3. **根本原因 (Root Cause)**: 仕様不備 / ロジックミス / タイミング / ハードウェア要因
   - 対象: バグ
4. **レビュー担当者 (Reviewer)**: ユーザー選択
   - 対象: タスク、成果物
   - 運用ルール: 「担当者」とは別に設定し、完了時に承認を得ること。

## Section 2: Redmine 運用ルール & Wikiテンプレート
開発者が参照するルールブックと、Redmine Wikiに貼り付けるトップページのテンプレートです。

1. **運用ルール**:
   - 「迷ったら『00_SystemDesign』に起票する」ルールの説明。
   - エピック(親)とバージョン(スプリント)の関係。
   - QAチームによる「完了」判定のプロセス。
2. **Wikiテンプレート (Markdownコードブロック)**:
   - `00_SystemDesign` プロジェクトのWikiトップページ用。
   - 項目: 「最新アーキテクチャ図」「I/F仕様書一覧」「技術トリアージルール」「新規参画者向けガイド」。

## Section 2.5: 完了の定義 (Definition of Done) チェックリスト
開発者がチケットを「完了」にする前に確認すべきチェックリストを、Markdownのチェックボックス形式で作成してください。
Wikiのサイドバーやテンプレートに埋め込むことを想定しています。
1. **実装タスクのDoD**:
   - [ ] GitLabのMRがマージされていること
   - [ ] 単体テストがパスしていること
   - [ ] 静的解析(Linter)のエラーがないこと
2. **バグ修正のDoD**:
   - [ ] 再現手順で現象が発生しないことを確認したか
   - [ ] 他の機能への影響(回帰)がないか確認したか
3. **成果物のDoD**:
   - [ ] 上長またはアーキテクトの承認ログがあるか

## Section 3: GitLab 初期設定・運用ガイド
1. **リポジトリ構成方針**:
   - Redmineの子プロジェクト（01~05）と1対1でリポジトリを作成する方針。
   - ディレクトリ構成ルール（`/src`, `/docs`, `/tests`）。
2. **Docs as Code運用**:
   - 機能設計書をMarkdownで `/docs` に格納するルール。
   - Redmineとの連携（コミットメッセージに `#TicketID` を含めるルール）。

## Section 4: GitLab README.md テンプレート
各リポジトリのトップに配置する `README.md` のテンプレート（Markdownコードブロック）。
以下の要素を含めてください。
- プロジェクト概要
- 関連するRedmineプロジェクトへのリンク
- ドキュメントの場所（`/docs` への誘導）
- 環境構築・ビルド手順のプレースホルダー

# Tone & Style
- 専門的かつ実践的。
- 曖昧な表現を避け、「～すること」と断定的に記述。
- エンジニアがコピペして使える品質を目指す。
## Specific of Style of FlowChart
フローチャート仕様は以下のとおりです。VisioのFlowchartテンプレート風で、モダンなデザインのフロー図をMermaid形式で作成してください。
### レイアウト
- 全体のフローは縦方向（トップダウン）で統一する。
- マーメイド記法内で定義された「participant」ごとに、縦のスイムレーンを1つずつ配置する。
- スイムレーンの枠線は薄いグレー（# CCCCCC）、背景は白。
- 各ステップは、対応する participant のスイムレーン内に必ず配置する。
### 図形スタイル
- プロセス：角丸長方形（Rounded Rectangle）、塗り白、枠線 # 4A90E2、影は軽く。
- 自動処理や内部処理と推定されるステップ（participant 自身への矢印や自己呼び出しなど）：淡いブルー (# E8F1FF) の角丸長方形。
- 外部からの入力や受信と推定されるステップ（他 participant からのメッセージ）：淡いグリーン (# E9F7EC) の角丸長方形。
- 条件分岐（alt / else / opt などのブロック）は菱形（Diamond）を使い、枠線色 # 7B61FF。
- 図形内テキストは中央揃え。
### 矢印（フローライン）
- すべて直線または 90 度折れ線で統一し、色はダークグレー（# 555555）。
- 矢印ヘッドは明確で視認性の高いスタイルにする。
- 条件分岐は菱形の下から左右に分岐する Visio 標準構造を採用し、alt / else ラベルを付与する。
### アイコン
- 図形左上に、処理の性質を示すフラットアイコンを小さく配置する（例：人物、サーバー、AI、入出力、プロセスなど）。
- アイコンの線幅は 1.5〜2px、統一感を持たせる。
- アイコンの具体的種類は participant 名や処理内容に応じて自動的に適切なものを割り当てる。
### 色の統一
- 背景：淡いグレー（# F7F7F7）
- 一般プロセス：白
- 内部処理（自動／自己呼び出し）：淡いブルー (# E8F1FF)
- 受信／入力類：淡いグリーン (# E9F7EC)
- 分岐ラベル：濃いグレー (#444444)
### フォント
- サンセリフ体（Segoe UI, Helvetica, Noto Sans など）
- 図形内テキスト：18px前後
- ラベル（alt, else, opt）：14px
### スペーシング
- 図形間の垂直距離は 40〜60px に統一。
- スイムレーンは均等な幅で揃える。
- 全体のマージンを確保し、図形の水平位置は揃えて整然と配置する。
### 全体の雰囲気
- モダンでシンプルな UI 風デザイン。
- 装飾を少なめに抑え、視認性重視。
- 影はごく軽く、過度な立体表現は避ける。
- 全体形状のバランスと整列を明確に保つ。

```
