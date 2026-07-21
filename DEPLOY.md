# 公開手順 — GitHub + Vercel

このサイトは静的な1ファイル（`index.html`）なので、**ビルド設定は不要**です。
以下はあなたのMacの「ターミナル」または「GitHub Desktop」で行ってください
（GitHub / Vercel へのログインが必要なため、この作業だけは手元で実行します）。

--------------------------------------------------
## STEP 1. GitHub にコードを上げる
--------------------------------------------------

### 方法A：ターミナル（コピペでOK）

```bash
cd ~/Desktop/HAYOUNG\ LEE
git init
git add .
git commit -m "Initial commit: Hayoung Lee portfolio"
git branch -M main
```

次に github.com で空のリポジトリを作成します（例：`hayoung-lee-portfolio` / Public か Private はお好みで。README等は追加しない）。
作成後に表示される URL を使って：

```bash
git remote add origin https://github.com/<あなたのユーザー名>/hayoung-lee-portfolio.git
git push -u origin main
```

初回 push で GitHub のログイン（ブラウザ認証）が求められたら承認してください。

### 方法B：GitHub Desktop（GUI派向け）

1. GitHub Desktop を開く →「Add」→「Add Existing Repository」→ `~/Desktop/HAYOUNG LEE` を選択
2. 「create a repository」と出たら作成 → 「Publish repository」で GitHub に上げる

--------------------------------------------------
## STEP 2. Vercel で公開する
--------------------------------------------------

1. https://vercel.com にログイン（GitHubアカウントでログインすると連携が楽）
2. 「Add New…」→「Project」
3. STEP1で作った GitHub リポジトリを「Import」
4. 設定はデフォルトのままでOK：
   - **Framework Preset：Other**（Next.js等は選ばない）
   - **Build Command：空でOK**（ビルド不要）
   - **Output Directory：空 / ルートのまま**
   - `index.html` がルートにあるので自動でトップページになります
5. 「Deploy」を押す → 数十秒で `https://xxxx.vercel.app` の公開URLが発行されます

--------------------------------------------------
## STEP 3. 独自ドメイン（任意・後からでOK）
--------------------------------------------------

Vercel のプロジェクト → Settings → Domains で、取得済みドメイン
（例：`hayoung-lee.com`）を追加し、表示されるDNS設定を反映すれば独自URLになります。

--------------------------------------------------
## 以後の更新フロー
--------------------------------------------------

`index.html` を編集したり `assets/` に本番素材を入れたら：

```bash
cd ~/Desktop/HAYOUNG\ LEE
git add .
git commit -m "Update assets / text"
git push
```

push すると Vercel が**自動で再デプロイ**します（1分ほどで反映）。

--------------------------------------------------
## メモ
--------------------------------------------------
- ビルドは不要。`vercel.json` も無しでそのまま動きます。
- 画像・音源・実テキストの差し替え方法は `README.md` を参照。
- 連絡先メールは `index.html` の CONFIG に `glory91126@gmail.com` を設定済み。
