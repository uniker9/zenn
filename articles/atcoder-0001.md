---
title: "Hello AtCoder and online-judge-tools/oj"
emoji: "🏅"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: []
published: false
---

AtCoder を始めてみる。
ブラウザのテキストフィールドにコードを入力して…という方法を試した後、よりクールにいきたかったので online-judge-tools/oj を使って投稿してみた。

試した問題は、 [AtCoder Beginners Selection](https://atcoder.jp/contests/abs) の最初の練習問題 PracticeA (https://atcoder.jp/contests/abs/tasks/practice_1)。

## oj のインストール

[公式サイト](https://github.com/online-judge-tools/oj/blob/master/docs/getting-started.ja.md) に記された手順にしたがってインストールした。

## テスト環境作成

[online-judge-toolsを導入しよう！](https://blog.masutech.work/posts/compro/oj-introduction/) のアドバイスにしたがって、AtCoder用のディレクトリ atcoer と、その配下に今回の問題用のディレクトリ practiceA を作成した。

```sh
$ mkdir atcoder
$ cd atcoder
$ mkdir practiceA
```

そして、practiceA ディレクトリの下で、`$ oj d {問題ページのURL}` を実行した。

```sh
$ cd practiceA
$ oj d https://atcoder.jp/contests/abs/tasks/practice_1
```

この結果、practiceA 配下にテスト用データが格納された test ディレクトリがダウンロードされた。 

## プログラム作成

atcoder ディレクトリの下に、次のような内容の python プログラム practiceA.py （回答例そのもの）を作成した。

```python
a = int(input())
b, c = map(int, input().split())
s = input()
print("{} {}".format(a+b+c, s))
```

ここまでで、atcoder/practiceA ディレクトリの下は次のようになっている。

```bash
$ ls -1R  
practiceA.py
test

./test:
sample-1.in
sample-1.out
sample-2.in
sample-2.out
```


## テスト

atcoder/practiceA ディレクトリで次のようなコマンドを実行してテストする。

```sh
$ oj t -c "python3 practiceA.py" -d test
```

すると、コマンドの後に次のような結果が表示される。
```
[INFO] online-judge-tools 11.1.1 (+ online-judge-api-client 10.7.1)
[INFO] 2 cases found
time: illegal option -- f
usage: time [-lp] <command>
[WARNING] GNU time is not available: time

[INFO] sample-1
[INFO] time: 0.054032 sec
[SUCCESS] AC

[INFO] sample-2
[INFO] time: 0.063664 sec
[SUCCESS] AC

[INFO] slowest: 0.063664 sec  (for sample-2)
[SUCCESS] test success: 2 cases
```

AC はテストに通った事を意味している。

## 投稿

atcoder/practiceA ディレクトリで

```sh
$ oj s practiceA.py
```

と実行するだけでよい。
これにより、AtCoder に practiceA.py がアップロードされ、その合否判定結果がブラウザに表示される。

## さらにクールに

* [Windows 10 上で atcoder-cli を online-judge-tools と連携させて使う：導入からテストと提出までの基本的操作](https://hamukichi.hatenablog.jp/entry/2020/06/02/225148) で紹介されているように、 atcoder-cli を併用すればさらにクール。
* [Python と VSCode で競プロ - 標準入力の簡易化とサンプルケース判定の自動化 -](https://qiita.com/ajim/items/4d350710ba70056f5f6f) のように、VS Code のタスクとして設定すればさらにクール。
