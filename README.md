# slide-generator

## 目的  
ChatGPTで作成したセミナー構成・本文・図解指示・講師メモをもとに、**PowerPoint互換のスライド資料を安定して生成・管理できる仕組み**を提供します。

## 想定ユーザー
- 中学生・高校生アスリート
- 保護者
- スポーツ指導者

## このリポジトリでできること
- スライド構成をMarkdownまたはYAMLで管理
- PowerPoint用スライド原稿の整理
- `python-pptx`で.pptxファイル生成
- HTMLプレビュー自動作成
- Copilot等による拡張性の高い設計
- 明快なデザインルール管理

## できないこと
- 完全自動の凝ったスライドデザイン
- AIによるコンテンツ自動生成（構成はChatGPT等で事前生成必須）
- PowerPoint以外の形式変換

## 基本ワークフロー
1. セミナー構成をChatGPTでYAML化
2. examples/ に配置
3. `python src/build_html_preview.py [yaml]`
4. `python src/build_pptx.py [yaml]`
5. outputs/ からダウンロード
6. PowerPointで最終調整
7. OneDrive等に保存・共有
8. 改善点はIssueに

## セットアップ方法
```bash
python -m venv .venv
. .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## スライド生成方法

**HTMLプレビュー生成：**
```bash
python src/build_html_preview.py examples/growth_nutrition_for_junior_athletes.yaml
```

**PowerPoint生成：**
```bash
python src/build_pptx.py examples/growth_nutrition_for_junior_athletes.yaml
```

**テスト：**
```bash
pytest
```

## ディレクトリ構成
- 各種policy/ワークフロー/参考YAML/ソース/テンプレート/tests で構成

## PowerPoint互換性の注意
- 16:9, 標準フォント, アニメーションなし
- 文字画像化禁止
- レイアウトや色は `templates/pptx/theme_config.yaml`に準拠

## 今後の拡張予定
- サンプル増強・デザインルール自動チェック
- スピーカーノート自動出力
- Gensparkレベルの自動レイアウト
- Web UI連携
