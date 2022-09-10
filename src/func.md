<script src="https://cdn.lordicon.com/xdjxvujz.js"></script>

# 関数

関数は，引数と呼ばれる入力値を受け取り，任意の型の値を1つ返すことができます．L4Tでは，引数は最大6個まで受け取れます．

以下の関数を宣言したとしましょう．

```
func swap(array<num>[100] arr, num index1, num index2) -> num
  num tmp
  tmp: arr[index1]
  arr[index1]: arr[index2]
  arr[index2]: tmp
  return 0

```

これは，[4.4章 ポインタ](/types/ptr.html)の**Code examples**で書いた関数に似ていますが，実は少し違います．

実際にこの関数を使うと何が起こるか，下のコードを<a href="http://35.247.86.97/" target="_blank"><u>**L4T Playground**</u></a>で実行して見てみましょう．

```
func swap(array<num>[100] arr, num index1, num index2) -> num
  num tmp
  tmp: arr[index1]
  arr[index1]: arr[index2]
  arr[index2]: tmp
  return 0

func main() -> num
  array<num>[100] arr
  arr[20]: 20
  arr[70]: 70

  printf("arr[20] = %d, arr[70] = %d\n", arr[20], arr[70])

  swap(arr, 20, 70)

  printf("arr[20] = %d, arr[70] = %d\n", arr[20], arr[70])

  return 0

```

配列の値が変化しないことを確認できたと思います．これは，[4.4章 ポインタ](/types/ptr.html)の**Code examples**で書いた関数では引数でポインタを受け取っていましたが，上のコードでは `array` を**deep copy**で受け取っているからです．つまり， `swap` 関数の中で参照している `arr` は， `main` 関数の `arr` とは別のアドレスにある別の変数です．その配列の中身を書き換えても， `main` 関数の `arr` に変化がないのは当然ですね．

このような引数の受け取り方は，**値渡し**と呼ばれます．一方で，[4.4章 ポインタ](/types/ptr.html)で書いた関数のような引数の受け取り方は，**ポインタ渡し**と呼ばれます．

用途に応じて，値渡しとポインタ渡しを使い分けましょう．

## <lord-icon src="https://cdn.lordicon.com/giaigwkd.json" trigger="loop" delay="1000" style="height:2em"></lord-icon>C言語では許されるがL4Tでは禁止されている関数

<small>この機能は開発中です</small>


