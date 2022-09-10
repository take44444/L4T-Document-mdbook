<script src="https://cdn.lordicon.com/xdjxvujz.js"></script>

# ポインタ

`ptr` 型には，変数のアドレスを格納することができます．

```
num a, b
ptr<num> p

a: b: 100

p: &a
*p: 200

p: &b
*p: 300
```

4行目で変数 `a` (と `b` )に `100` を代入した後，6行目で変数 `p` に 変数 `a` のアドレスを代入しています． `&a` というように，変数の前に `&` を付けると，その変数のアドレスを得ることができます．[3章 変数](/var.md)で，変数の実体はメモリ上にあることもレジスタ上にあることもあると説明しましたが，コード上で， `&a` というような使い方をしている変数は，L4Tコンパイラによってメモリ上に割り当てられることが保証されています．

その後7行目で `*p: 200` と書いてありますが，これは，ポインタ `p` に格納されているアドレスに `200` を格納するということを意味します．よって，ここで変数 `a` の値は `200` になります．

9~10行目でも同様に，変数 `b` に格納されている値が `300` になります．

```
func main() -> num
  num a, b
  ptr<num> p

  a: b: 100

  p: &a
  *p: 200

  p: &b
  *p: 300
  printf(&"a = %d, b = %d\n", a, b)

  return 0

```

このコードを<a href="http://35.247.86.97/" target="_blank"><u>**L4T Playground**</u></a>で実行して， 

```
a = 200, b = 300
```

と表示されることを確認してみましょう！ 

他にも，配列のポインタや構造体のポインタ，ポインタのポインタも扱うことができます．

**ポインタは，"低レベル"プログラミングにおいて多くの人が最初につまづく概念**です．下のポインタを使ったコードの例を見たり，自分で書いてみるなどして，少しずつ慣れていきましょう！

## Code examples

### 関数の引数にポインタを使う例

```
func swap(ptr<array<num>[100]> arr_p, num index1, num index2) -> num
  num tmp
  tmp: (*arr_p)[index1]
  (*arr_p)[index1]: (*arr_p)[index2]
  (*arr_p)[index2]: tmp
  return 0

func main() -> num
  array<num>[100] arr
  arr[20]: 20
  arr[70]: 70

  printf("arr[20] = %d, arr[70] = %d\n", arr[20], arr[70])

  swap(&arr, 20, 70)

  printf("arr[20] = %d, arr[70] = %d\n", arr[20], arr[70])

  return 0

```

[関数](/func.html) `swap` は，配列のポインタと2つの整数 `index1` と `index2` を引数として受け取り，配列の `index1` 番目の値と `index2` 番目の値を交換します．配列のアドレスを引数として受け取るため， `main` 関数内の変数である配列 `arr` の中身を書き換えることができます．このコードを<a href="http://35.247.86.97/" target="_blank"><u>**L4T Playground**</u></a>で実行して， `arr[20]` と `arr[70]` の値が実際に入れ替わっていることを確認しましょう！

### ヒープ領域にメモリを確保する例

下のコードは，ヒープ領域に\\(8 \times 2 = 16\\)バイトのメモリを確保し，その場所を長さが\\(2\\)の配列として使っています．

```
extern "C" any malloc
extern "C" any printf

func main() -> num
  ptr<array<num>[2]> arr
  arr: malloc(16)

  (*arr)[0]: 100
  (*arr)[1]: 200

  printf("%d, %d\n", (*arr)[0], (*arr)[1])

  free(arr)
  return 0

```

<lord-icon
  src="https://cdn.lordicon.com/giaigwkd.json"
  trigger="loop"
  delay="1000"
  style="height:2em">
</lord-icon> <small> `extern "C" any malloc` と `extern "C" any printf` は未実装であり，現在は1行目と2行目を除いたコードを書くことで同じ挙動を試すことができます．</small>
