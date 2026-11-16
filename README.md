# 電子回路計算ツール

回路設計でよく使う計算を、ブラウザだけで行うためのツール集です。

※いまのところ、あくまでも「こういうツール集があったらいいな」を試験する目的で作ったものであり、計算式や出力内容については未検証です。※

| ディレクトリ | ツール | 内容 |
|---|---|---|
| `voltage-divider/` | 可変抵抗分圧計算機 | 可変抵抗を2つの固定抵抗で挟む分圧回路。電圧範囲 ⇄ 固定抵抗の双方向計算、E系列への丸め、ワイパー位置スライダー、電流・消費電力 |
| `comparator-hysteresis/` | コンパレータヒステリシス計算機 | 反転型・非反転型、プッシュプル・オープンドレイン。しきい値 ⇄ 抵抗値の双方向計算、E系列への丸め、ヒステリシスループ、CircuitJS 用の回路の書き出し |
| `led-resistor/` | LED電流制限抵抗計算機 | 色・電源電圧・明るさから抵抗値を計算、手持ちの抵抗から電流を逆算、明るさシミュレーション、計算式の表示 |

トップの `index.html` が、3つのツールへのリンクを並べた親ページです。

## ファイル構成

```
.
├── index.html                    親ページ（ツール一覧）
├── .nojekyll                     GitHub Pages で Jekyll の処理を止める
├── voltage-divider/index.html
├── comparator-hysteresis/index.html
└── led-resistor/index.html
```

各ツールは CSS と JavaScript を1つの HTML に含んだ単独のファイルです。ツール間で共有するファイルはありません。

## ローカルで確認する

```bash
python3 -m http.server 8000
```

ブラウザで http://localhost:8000/ を開きます。

## 外部への依存

- フォント: Google Fonts（IBM Plex Sans JP / IBM Plex Mono）。読み込めない場合はシステムフォントで表示されます。
- コンパレータヒステリシス計算機のみ: lz-string 1.5.0（cdnjs）。CircuitJS へのリンク用に回路データを圧縮します。読み込めない場合は非圧縮のリンク（`?cct=`）になります。
- 「CircuitJS で開く」は https://www.falstad.com/circuit/ の CircuitJS を開きます。
