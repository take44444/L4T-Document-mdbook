<script src="https://cdn.lordicon.com/xdjxvujz.js"></script>

# loop文

`loop` 文を使うことで，繰り返し処理を行うことができます．

```
num a
a: 0

loop a < 5
  printf("%d\n", a: a + 1)

```

`loop` 文は，条件式の値が `0` 以外である限り，中身のコードを繰り返し実行します．上のコードは， `a` の値が `5` より小さい限り `printf("%d\n", a: a + 1)` を繰り返すコードです．

下のコードを<a href="http://35.247.86.97/" target="_blank"><u>**L4T Playground**</u></a>で実行して，実際に動作を確認しましょう！

```
ffi "C" printf

func main() -> num
  num a
  a: 0
  loop a < 5
    printf("%d\n", a: a + 1)
  return 0

```

## break文とcontinue文

下のコードは，上のコードと同じ動作をします．

```
num a
a: 0

loop 1
  if a < 5
    printf("%d\n", a: a + 1)
    continue
  break

```

`continue` は，loop文の先頭に戻る文で， `break` はloopを抜け出す文です．
