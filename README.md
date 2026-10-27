# 白背景・青基調のプレゼンテーションテンプレート

Marp向けの16:9テンプレートです。`template.md`をコピーして本文を編集し、ページを増減できます。背景は白、見出しと強調は青、本文は濃い紺色です。

## ファイルとフォルダ

```text
marp/
├─ template.md           表紙・目次・章扉・本文・写真・比較・予定・締めの9ページ
├─ themes/
│  └─ blue-white.css     配色・文字サイズ・レイアウト
├─ assets/
│  ├─ photos/            写真の保存先
│  ├─ logos/             ロゴの保存先
│  └─ charts/            グラフ画像・図の保存先
├─ exports/              PDF・PowerPoint・HTMLなどの出力先
├─ .vscode/              Marpのテーマ設定と推奨拡張機能
└─ .marprc.yml           Marp CLI向け設定
```

## 編集とプレビュー

1. VS Codeでこの`marp`フォルダを開きます。
2. 推奨拡張機能の「Marp for VS Code」をインストールします。
3. `template.md`をコピーし、たとえば`presentation.md`として保存します。
4. Markdownのプレビューを開き、タイトル・本文・フッターを書き換えます。
5. `---`がページの区切りです。必要なページを区切りごとコピーして使います。

写真レイアウトはHTMLを使います。HTMLを有効にする設定を同梱しています。VS Codeでフォルダの信頼設定が表示された場合は、内容を確認して設定してください。

## 写真の追加

写真を`assets/photos/`に保存します。写真ページの`<div class="photo-slot">…</div>`を削除し、次の行を同じ位置に入れます。ファイル名は保存した写真に合わせて変更してください。

```html
<img class="photo" src="assets/photos/photo-01.jpg" alt="写真の説明">
```

大きな写真ページでは`class="photo wide"`を使います。写真の下に説明と出典を記入します。画像は枠いっぱいに表示し、はみ出す部分を切り取ります。写真全体を見せたい場合は、テーマの`.photo`にある`object-fit: cover`を`object-fit: contain`に変更します。

ロゴは`assets/logos/`へ保存し、必要な位置に次のように追加できます。

```markdown
![w:160](assets/logos/company-logo.png)
```

## 配色とレイアウト

- メインの青：`#1557B0`
- 見出しの紺：`#14345B`
- 背景：`#FFFFFF`
- 写真枠などの淡い青：`#EDF4FC`
- 日本語フォント：游ゴシック、メイリオ

色は`themes/blue-white.css`冒頭の変数で変更できます。表紙は`cover`、章扉は`section`、締めは`closing`クラスを指定します。2段組みは`columns`クラスを使います。文章が収まらない場合はページを分けてください。

## 書き出し

VS Codeのコマンドパレットから「Marp: Export Slide Deck」を実行し、`exports/`へ保存します。利用できる形式は環境によって異なります。PDFやPowerPointへの出力には対応ブラウザが必要です。Marpの通常のPowerPoint出力はスライドを画像として格納するため、本文の編集はMarkdown側で行ってください。

Marp CLIを別途インストールしている場合は、プロジェクトのルートで以下を実行できます。

```powershell
marp presentation.md -o exports/presentation.html
marp presentation.md --pdf -o exports/presentation.pdf
marp presentation.md --pptx -o exports/presentation.pptx
```

写真やロゴを一緒に管理するため、資料を移動するときはフォルダ全体をコピーしてください。
