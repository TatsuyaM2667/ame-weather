# ame-weather

今の天気を wttr.in から取ってくる小さなコマンド(文字 / JSON)。

[ame-shell](https://github.com/TatsuyaM2667/ame-shell)(Wayland のデスクトップシェル)の一部を、単独で使えるように切り出したものです。
ame-shell は画面の要らない仕事を、1 つのことをして標準入出力でやりとりする小さなコマンドに分けています。これはその 1 つです。

## 使い方

```text
ame-weather: 今の天気を wttr.in から取ってくる。

  ame-weather [-l 言葉] [場所]          「12°C 晴れ(Sapporo, Japan)」の 1 行
  ame-weather --json [-l 言葉] [場所]   {"temp","condition","symbol","icon","place"} の 1 行

場所を省くと IP アドレスから推定。言葉は既定 ja(wttr.in の lang)。icon は Nerd Font の天気のアイコン(夜は月)。
終了コード: 0 取れた / 1 場所が分からない・返事の形が違う / 2 つながらない(curl が要る)
```

## ビルド

```sh
zig build -Doptimize=ReleaseSafe   # zig-out/bin/ame-weather(Zig 0.13、libc だけ)
zig build test
```

実行に要るもの: `curl`

## このリポジトリについて

正本は ame-shell の `src/cmd/ame-weather.zig` です。このリポジトリは `scripts/split-repos.sh` が生成して同期しています。
直したいところがあれば ame-shell の方へお願いします。

ライセンス: GPL-3.0(ame-shell と同じ)
