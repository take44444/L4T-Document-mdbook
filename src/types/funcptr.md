<script src="https://cdn.lordicon.com/xdjxvujz.js"></script>

# 関数ポインタ

`funcptr` 型には，関数のアドレスを格納することができます．

関数ポインタは，下のコードのようにして宣言します．

```
funcptr (num) -> num fp
```

これは， `num` 型の値を1つ引数として受け取り `num` 型の値を返す関数のアドレスを格納することができる関数ポインタです．

下のコードは， `funcptr` 型の配列を宣言し，そこに `add` 関数と `sub` 関数のアドレスを代入し，その配列を使って関数を呼び出しています．

```
func add(num x, num y) -> num
  return x + y

func sub(num x, num y) -> num
  return x - y

func main() -> num
  array<funcptr (num, num) -> num>[2] funcp_arr

  funcp_arr[0]: add
  funcp_arr[1]: sub

  printf("%d\n", funcp_arr[0](100, 200))
  printf("%d\n", funcp_arr[1](100, 200))
  return 0

```