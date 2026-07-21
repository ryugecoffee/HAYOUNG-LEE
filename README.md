# HAYOUNG LEE — Portfolio (差し替えガイド)

`index.html` 1ファイルで完結しています。ブラウザで開くだけで動作します。
編集は基本 **`index.html` 内の `CONFIG`（`<script>` 先頭）1か所** だけでOKです。

## 1. 画像の差し替え
このフォルダに `assets/` を作り、画像を置いて `CONFIG.assets` にパスを書きます。

```js
assets:{
  guitarNormal:"assets/guitar-normal.webp", // 通常ギター（正面・同構図）
  guitarFantasy:"assets/guitar-fantasy.webp",// 幻想ギター（★通常版と完全に同じ構図・同じ位置）
  magpie:"assets/magpie.png",                // カササギ（透過PNG推奨）
  portrait:"assets/hayoung.webp",            // ABOUTのプロフィール写真
}
```
※ 空文字のままなら、内蔵のSVGプレースホルダーが表示されます。
※ 幻想版は「通常版と同じ構図で撮る／作る」ことが最重要です（重ねてマスク表示するため）。

## 2. 音源の差し替え
6弦分の短い単音（E2 A2 D3 G3 B3 E4）を置いて指定します。空なら合成音になります。
```js
audio:{ strings:[
  "assets/string-e-low.mp3","assets/string-a.mp3","assets/string-d.mp3",
  "assets/string-g.mp3","assets/string-b.mp3","assets/string-e-high.mp3"], ... }
```

## 3. テキスト（3言語）
`I18N.en / I18N.es / I18N.kr` に全文言があります。仮訳なので上書きしてください。
公演・レパートリー・受賞・リンクは `CONFIG.concerts / repertoire / awards / links` を編集。

## 4. 連絡先メール
現在 `glory91126@gmail.com` を仮設定。公開して良いアドレスか確認のうえ `CONFIG.links.email` を変更してください。

## 実装済みの演出
- カーソル/指がギター領域内のときだけ、周辺に円形マスクで幻想版が出現（背景・文字は不変）
- ゆっくりなぞると金の光・花・花びらが増える／速いと控えめ
- 6弦のヒット判定＋Web Audio音＋弦の振動（Sound On/Off・自動再生制限対応）
- サウンドホール付近をゆっくり／幻想度が上がると、カササギが一羽だけ現れて数秒で飛び去る（隠し演出）
- スマホ：横方向/ギター上の指移動で反応、縦スワイプはスクロール優先、長押しで強調
- prefers-reduced-motion 対応、遅延読み込み、コントラスト確保
