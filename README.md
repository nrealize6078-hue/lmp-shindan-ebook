# LMP経営診断書 ― 御社なら、どう勝つか。

LIFE MAKE PARTNERS の個別事業診断フォーマット（全12項目＋総合診断）を電子書籍化したもの。
[lmp-playbook-ebook](https://github.com/nrealize6078-hue/lmp-playbook-ebook) と同じ体裁で組んでいる（配色のみスカイブルー）。

## 成果物

| ファイル | 内容 |
|---|---|
| `index.html` | 電子書籍。単一ファイル完結。GitHub Pages にそのまま置ける |
| `LMP_SHINDAN_A4.pdf` | A4縦 10ページ版（印刷して手書き記入できる版面） |
| `cover.png` / `back.png` | 表紙・裏表紙（A4版PDFの1ページ目・10ページ目から生成） |

A4版PDFの版面は `~/lmp-journey-pdf/shindan.html`。Chrome の `--print-to-pdf` で刷っている。

```bash
"C:/Program Files/Google/Chrome/Application/chrome.exe" --headless=new --disable-gpu \
  --no-pdf-header-footer --print-to-pdf="LMP経営診断書.pdf" "file:///.../shindan.html"
```

刷り直したら、表紙画像も作り直す。

```bash
pdftoppm -f 1 -l 1 -r 180 -png -singlefile "LMP_SHINDAN_A4.pdf" cover
pdftoppm -f 10 -l 10 -r 120 -png -singlefile "LMP_SHINDAN_A4.pdf" back
```

## 構成

底本（Googleドキュメント「LMP　経営診断書」）の 01〜12 と総合診断を、そのまま章立てにしている。

- **序** … この診断書について
- **第1部　御社を知る** … 01 大切にしていること／02 現在の経営課題／03 すでに持っている「資産」
- **第2部　御社の型を見立てる** … 04 LMPタイプ／05 経営エンジン
- **第3部　これからの広がり** … 06 収益拡張MAP／07 顧客基盤拡張MAP
- **第4部　実行と条件** … 08 最初の90日／09 エリア診断／10 収益シミュレーション
- **第5部　本部所見と未来** … 11 本部から見た可能性／12 目指す未来／総合診断

## 底本の扱い

見出し・項目名・選択肢・数値は底本にあるものだけを使っている。
読み物として成立させるための地の文（序と各部の扉のリード）は、底本の LMP Lステップ本文
（「相手を理解してから、提案する。」「1エリア2社程度。」など）から採っている。
推測で数値・実績を足していない。

## 記入欄について

電子書籍版の記入欄は、紙面と同じ体裁を再現した表示のみ（入力はできない）。
実際に記入する場合は A4版PDF を印刷して使う。
画面上で入力・保存できるようにすることも可能（localStorage 保存 ／ 未実装）。

## プレビュー

`.claude/launch.json` に `lmp-shindan`（ポート 3490）として登録済み。
