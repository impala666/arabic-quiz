# アラビア文字 読み方クイズ

アラビア文字28字の読み方を3択で確認し、苦手をヒートマップで可視化

スマートフォンにインストールして使える、単一ページのWebアプリ（PWA）です。
学習の記録は端末のブラウザ内にだけ保存されます。サーバーへは何も送信しません。

## GitHub Pages への置き方

1. GitHub で**公開リポジトリ**を新規作成する（名前はたとえば `arabic-quiz`）
2. このフォルダの中身を、リポジトリの**直下**にそのまま置く
   - ブラウザからなら、リポジトリ画面の `Add file` → `Upload files` に
     5つのファイルをまとめてドラッグし、`Commit changes`
   - コマンドからなら:
     ```
     git init
     git add .
     git commit -m "first commit"
     git branch -M main
     git remote add origin https://github.com/<ユーザー名>/arabic-quiz.git
     git push -u origin main
     ```
3. リポジトリの `Settings` → `Pages` を開く
4. `Source` を **Deploy from a branch**、`Branch` を **main** / **/(root)** にして `Save`
5. 1〜3分ほど待つと次のURLで公開されます

   `https://<ユーザー名>.github.io/arabic-quiz/`

## スマホにアプリとして入れる

- **Android（Chrome）**: 上のURLを開く → 右上の︙ →「アプリをインストール」
  （出ないときは「ホーム画面に追加」）
- **iPhone（Safari）**: 上のURLを開く → 共有ボタン →「ホーム画面に追加」

ホーム画面のアイコンから起動すると、アドレスバーのない単独アプリとして開きます。
一度開いたあとは、機内モードでも起動します。

## 中身

| ファイル | 役割 |
|---|---|
| `index.html` | アプリ本体。HTML・CSS・JavaScript がこの1枚に入っています |
| `manifest.webmanifest` | アプリ名・アイコン・全画面表示の設定 |
| `sw.js` | オフラインで開くためのキャッシュ |
| `icon-192.png` / `icon-512.png` | ホーム画面のアイコン |

## 更新のしかた

`index.html` を書き換えて push すれば、そのまま反映されます。
ただし `sw.js` が古い版をキャッシュしているため、画面が変わらないことがあります。
その場合は `sw.js` の1行目付近にある

```
const CACHE = "arabic-quiz-v1";
```

の `v1` を `v2`、`v3` …と上げてから push してください。古いキャッシュが破棄されます。

## 記録の持ち運び

学習の記録はアドレス（オリジン）ごとに保存されるため、
`claude.ai` で貯めた記録や、別のドメインの記録は自動では引き継がれません。
アプリ内の「データのバックアップ・復元」から JSON ファイルを書き出し、
移行先で読み込ませてください。
