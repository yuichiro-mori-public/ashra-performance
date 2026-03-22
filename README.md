# Ashra Performance

複数の Android 端末でマスゲーム/LED マトリクス表示を行うための静的ページ。

## 仕組み

各端末がこのページを開き、URLパラメータで受け取った位置情報に基づいて、
フレームデータから自分の色を全画面表示する。

## URL パラメータ

| パラメータ | 型 | 説明 |
|-----------|-----|------|
| `frames_url` | string | フレームJSON のURL |
| `x` | int | グリッド上の列位置 (0-indexed) |
| `y` | int | グリッド上の行位置 (0-indexed) |
| `fps` | int | フレームレート (default: 10) |
| `serial` | string | デバイスシリアル (デバッグ表示用) |
| `start` | int | 開始 Unix タイムスタンプ (ms)。同期用 |
| `text` | string | Blink互換: フレーム不使用、テキスト表示のみ |

## フレーム JSON 形式

```json
{
  "frames": [
    [                       // frame 0
      ["#ff0000", "#00ff00", ...],  // row 0
      ["#0000ff", "#ffff00", ...],  // row 1
      ...
    ],
    ...                     // frame 1, 2, ...
  ]
}
```

## 使用例

```
https://<your-gh-pages>/ashra-performance/?frames_url=https://example.com/frames.json&x=3&y=1&fps=10&start=1711234567890
```

## デプロイ

GitHub Pages で公開。`main` ブランチの `/` をソースに設定。
