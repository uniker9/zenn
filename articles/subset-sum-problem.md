---
title: "部分和の列挙"
emoji: "🎰"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Atcoder", "Python3"]
published: true
---

集合の部分和を列挙する方法を学んだ。
※集合 a = {8 3 7 2 5} に対する {0, 2, 3, 5, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 20, 22, 23, 25} のようなもの。

```
    a = map(int, input().split())
    sub = set()
    sub.add(0)
    for i in a:
        for j in list(sub):
            sub.add(i+j)
```

より短く次のようにも書ける（のを知った）。

```
    a = map(int, input().split())
    sub = {0}
    for i in a:
        sub |= {i + j for j in sub}
```

なお、集合 set に追加した部分和をソートするには、

```
sorted(list(sub))
```

とする。
`list(sub)` は `[*sub]` というようにも書ける（ことも知った）。
