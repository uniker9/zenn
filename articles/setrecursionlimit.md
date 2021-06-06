---
title: "python で再帰を使う場合には再帰上限数を増やしておく"
emoji: "⤴️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [AtCoder]
published: true
---

[AtCoder Beginner Contest 204](https://atcoder.jp/contests/abc204) で RE（Runtime Error）に遭遇。

何度コードを確認してみても原因分からず（RE いくつか増やしてしまった後に）検索してみたところ、 [AtCoder で RE の解消の仕方がわかりません という teratail の QA](https://teratail.com/questions/264222) に、次のように書かれているのを発見した。

> n>1000あたりで再帰回数がpythonの上限を超えランタイムエラーを起こします。
sys.setrecursionlimit()で再帰突入回数の上限を変更できます（デフォルトは通常1000）

これを参考に、自分のコードの冒頭に次の2行を付与して投稿したら AC とれた。

```
import sys
sys.setrecursionlimit(100000)
```

解説のサンプルコードにも同じように書かれていたので、これは定石なのだろう。
今週も一つ学びを得た。
