# 目標図鑑

パチンコ・パチスロの演出目標を年ごとに管理し、達成したら写真を貼って記録する個人用Webアプリ（PWA）です。
データは端末のブラウザ内（localStorage）にのみ保存され、外部には送信されません。

## ファイル構成

```
goal-zukan/
├── index.html          本体（これを開けばそのまま使えます）
├── manifest.json        PWA設定（ホーム画面追加用）
├── service-worker.js    オフラインキャッシュ
└── icons/
    ├── icon-192.png
    ├── icon-512.png
    ├── icon-192-maskable.png
    ├── icon-512-maskable.png
    ├── apple-touch-icon.png
    └── favicon.ico
```

## GitHub Pagesへのデプロイ手順

1. GitHubで新しいリポジトリを作成します（例: `goal-zukan`）。
2. このフォルダの中身一式（`index.html` / `manifest.json` / `service-worker.js` / `icons/`）をリポジトリのルートに追加します。

   ```
   git init
   git add .
   git commit -m "goal-zukan: initial commit"
   git branch -M main
   git remote add origin https://github.com/syota1217/goal-zukan.git
   git push -u origin main
   ```

3. GitHubのリポジトリページで **Settings → Pages** を開きます。
4. **Source** を「Deploy from a branch」、**Branch** を `main` / `/(root)` に設定して保存します。
5. 数分後、`https://syota1217.github.io/goal-zukan/` でアクセスできるようになります。

## ホーム画面に追加する（PWA化）

- **iPhone (Safari)**: サイトを開き、共有ボタン → 「ホーム画面に追加」
- **Android (Chrome)**: サイトを開き、メニュー → 「ホーム画面に追加」/「アプリをインストール」

ホーム画面から起動すると、ブラウザのアドレスバーなどが表示されないアプリのような見た目で使えます。
`service-worker.js` により一度開いたページはオフラインでも起動できます（新しいデータの保存自体はオンライン・オフラインどちらでも可能です。写真や目標はすべて端末内保存です）。

## 注意

- データのバックアップはアプリ内の「エクスポート」ボタンからJSONファイルとして保存できます。機種変更時などは「インポート」で復元してください。
- ブラウザのキャッシュ・サイトデータを削除するとデータも消えるため、定期的なエクスポートをおすすめします。
