# AGENTS.md

AI コーディングエージェント共通の作業ガイド。
ツール固有の補足は各ファイルに分離し、ここではこのリポジトリで共通に守る方針のみを記す。

## プロジェクト概要

- 目的: GitHub Copilot を使った開発作業を、メンバーが START（仕様書）から GOAL（PR）まで迷わず進めるための運用フローとプロンプト雛形として整理する
- 対象: 2 ゲート制の開発ワークフロー、8 ステップのチェックリスト、GCP / MLOps / Terraform 向けの Copilot プロンプト例
- 現状: コードを持たないドキュメント専用リポジトリ。成果物は Markdown のみ

## 基本方針

- ドキュメント間の整合性を最優先する
- 憶測で確定情報を書かない
- ワークフロー変更時は、正本である `src/01_workflow-guide.md` を先に更新し、`README.md` と `src/02_prompt-templates.md` を合わせる
- 確認フェーズではプロダクションコードもテストコードも書かない、という前提を崩さない
- 実装フェーズはテストファースト（テスト作成 → 実装）を前提にする
- AI が挙げた関数 / API / ライブラリ / 設定キー / DB カラムは、実物確認の証跡を残す

## 権威順位

```text
src/01_workflow-guide.md
> src/02_prompt-templates.md
> README.md
```

ツール固有の補足は [`CLAUDE.md`](CLAUDE.md) を参照する。

## 更新ルール

- ワークフローのステップ追加・削除・番号変更は `src/01_workflow-guide.md` と `src/02_prompt-templates.md` の両方に反映する
- README の全体像やドキュメント構成が変わる変更は、同一変更で `README.md` も更新する
- `src/01_workflow-guide.md` は運用ガイド本体、`src/02_prompt-templates.md` は各ステップに 1:1 対応するプロンプト例集として扱う
- 「作業計画書」は必須提出物、「実装サンプルメモ」は任意・自分用でリーダー提出不要。この区別を崩さない
- 実在確認の詳細手順は `src/02_prompt-templates.md` に集約し、ガイド側は要点に留める
- 関連ドキュメントは同一変更でまとめて更新する

## 作業上の注意

- ビルド / lint / test / 実行コマンドは存在しない前提。検証は Markdown の整合性確認が中心
- ドキュメント・コミットメッセージ・PR タイトルは日本語を canonical とする
- Mermaid 図、チェックリスト、プロンプト雛形のステップ番号がずれないように確認する
- プロンプト集は GCP（Vertex AI / BigQuery / Cloud Run Jobs / Elastic Cloud）/ Terraform を中心とした MLOps 基盤を前提にしている。前提を変える場合は前提欄と例文を合わせて更新する
