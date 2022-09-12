<script src="https://cdn.lordicon.com/xdjxvujz.js"></script>

# if-elif-else文

`if-elif-else` 文を使うことで，条件分岐を行うことができます．

```
func is_zero(num x) -> num
  if x
    return 0
  else
    return 1

```

上の関数は，引数で受け取った `x` の値が `0` であれば `1` を，それ以外の場合は `0` を返す関数です．2行目の `if` 文 では， `if` の横に来た値が `0` 以外の場合はその直後の[**ブロック**](./compound.html)が実行されます． `else` 文の直後のブロックは，直前の `if` ( `elif` )で値が `0` だった場合に実行されます．

`else` 文は，直前に `if` ( `elif` )文がないと使えません．
