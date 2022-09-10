<script src="https://cdn.lordicon.com/xdjxvujz.js"></script>

# Hello, world!

```
extern "C" any printf

func main() -> num
  printf(&"Hello, world\n")
  return 0

```

<lord-icon
  src="https://cdn.lordicon.com/giaigwkd.json"
  trigger="loop"
  delay="1000"
  style="height:2em">
</lord-icon> <small> `extern "C" any printf` は未実装であり，現在は1行目を除いたコードを書くことで同じ挙動を試せます．</small>

上のコードを実行すると，標準出力に

```
Hello, world!
```

と出力されます．

3行目の `func main() -> num` は，[関数](/func.html)を定義しています．L4Tでは，プログラムは `main` 関数の中身から実行されます．プログラム内で，コンピュータが最初に実行する場所は**エントリポイント**と呼ばれます．言い換えればL4Tでのエントリポイントは `main` 関数であり， `main` 関数のないコードはL4Tではコンパイルされません．

`-> num` は，この `main` 関数の返り値が `num` 型であることを示しています．分かりやすいですね！

4~5行目には，2つのスペースが先頭にあります．これは**インデント**と呼ばれ，4行目と5行目のコードがこの `main` 関数内の処理であることを意味します．

4行目では，`printf` という関数を呼び出しています．しかし， `printf` 関数の定義はコード上にありませんね．これは，1行目の `extern "C" any printf` と関係しています．詳しくは，[10章 FFI](/ffi.html)で説明します．ここでは単に， `printf` 関数は文字列を表示する関数だと認識しましょう．

5行目の `return 0` は， `0` という値を返すとともに `main` 関数を終了する文です． `main` 関数の返り値は，プログラムの終了コードとなります．このプログラムは，終了コード `0` で終了します．
