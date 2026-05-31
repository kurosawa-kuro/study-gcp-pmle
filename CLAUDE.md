# CLAUDE.md

このファイルは Claude Code (claude.ai/code) がこのリポジトリで作業する際のガイドを提供する。

## プロジェクトの性質

PMLE（Google Cloud Professional Machine Learning Engineer）合格直結の**教材コンテンツ**リポジトリ。アプリ・DB・インフラは持たない。成果物は日本語 Markdown の「判断辞書型」教材（章原稿 + 比較表 + シグナル語辞典 + 判断フローチャート）。設計意図は [`doc/01_仕様と設計.md`](doc/01_仕様と設計.md) を正とする。

## コマンド

ターゲット名は維持（Makefile 注記）。中身はコンテンツ教材向けの意味で実装する。

```bash
make setup    # ツール取得 (markdownlint 等)
make fmt      # Markdown 整形
make lint     # markdownlint / 静的検証
make test     # リンク切れ・フォーマット検証
make build    # 配布物生成 (静的サイト / PDF 化。配布形態が確定するまで TODO)
make dev      # プレビュー (Markdown プレビュー)
```

## アーキテクチャ

- 教材の章原稿は `src/` 配下に置く。
- 設計対象は教材の「構造」（章 = 意思決定単位、章テンプレートの統一）。詳細は [`doc/01_仕様と設計.md`](doc/01_仕様と設計.md)。
- 非機密の設定は `env/config.yaml`、ローカル秘密情報は `env/secret.yaml`、チーム共有・本番クレデンシャルは Doppler (`doppler.yaml`) で管理する。
- 設計・運用ドキュメントは `doc/` 配下。権威順位と更新規約は [`doc/README.md`](doc/README.md) に従う（`02_移行ロードマップ.md` が決定的仕様）。

## 作業ルール

- 推測で書かない。各「選ぶ / 選ばない」判断は GCP 公式ドキュメントで裏取りする。
- 章は全て `doc/01 §2.1` の 8 項目テンプレートで統一する。フォーマット逸脱を作らない。
- 仕様変更は連動するドキュメント（`doc/01`〜`doc/04`）を同一 PR で直す。drift を作らない。
- 公式試験ガイド改訂時は出題範囲・比率・対象サービスを見直す（`doc/01 §4` 鮮度要件）。
