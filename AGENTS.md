# AGENTS.md

AI コーディングエージェント（Claude Code / Codex / GitHub Copilot 等）共通の作業ガイド。
ツール固有の指示は各ツールのファイル（例: `CLAUDE.md`）に置き、ここには共通方針のみ記す。

## プロジェクト概要

- 目的: PMLE（Google Cloud Professional Machine Learning Engineer）合格直結の教材を作る。技術の網羅説明ではなく、**問題文の制約から正解サービス・構成・運用判断を選ぶ「判断辞書」**を作る。
- 主要技術: 日本語 Markdown のコンテンツ教材（アプリ・DB・インフラは持たない）。題材は GCP の AI/ML サービス群（BigQuery ML / AutoML / Vertex AI / Pipelines / Feature Store / Model Monitoring / Model Garden / Agent Builder / RAG 等）。

## セットアップ / 主要コマンド

```bash
make setup    # ツール取得 (markdownlint 等)
make fmt      # Markdown 整形
make lint     # markdownlint / 静的検証
make test     # リンク切れ・フォーマット検証
```

## 執筆規約

- 既存の章フォーマット・命名・パターンに合わせる。章は全て `doc/01 §2.1` の 8 項目テンプレートで統一する。
- 推測で書かない。各「選ぶ / 選ばない」判断は GCP 公式ドキュメントで裏取りする。
- 変更後は `make lint` / `make fmt` を実行してから完了とする。
- 非機密の設定値は `env/config.yaml`、ローカル秘密情報は `env/secret.yaml`、チーム共有・本番クレデンシャルは Doppler (`doppler.yaml`)。秘密情報をコミットしない。

## ドキュメント

設計・仕様・運用は `doc/` 配下を参照。更新規約と権威順位は [`doc/README.md`](doc/README.md) に従う。
仕様レベルの変更は連動するドキュメントを同一 PR でまとめて直す。
