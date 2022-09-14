<script src="https://cdn.lordicon.com/xdjxvujz.js"></script>

# 整数

`num` 型では，8バイトの符号付き整数を扱えます．`num` 型同士で，以下のような演算を行えます．

## 2項演算

### Assignment

代入演算は `:` で行います．

```
a: 10
```

`a` に `10` が代入されます．

```
b: a
```

`b` に `a` の値が代入されます．

```
a: b: 100
```

`b` に `100` が代入された後， `a` にも `100` が代入されます．これは，L4Tの代入は， **代入"文"ではなく代入"式"** であり，代入した値として評価されるからです．

### Logical Or

まず左の式を評価し，左の式が `0` のときのみ右の式を評価します．どちらも `0` のときは `0` と評価され，それ以外は `1` と評価されます．
[if-elif-else文](../if.html)や[loop文](../loop.html)と組み合わせて使うと便利です．

```
a: 5
b: 10
c: a < 4 || b > 10
```

`c` には `0` が代入されます．

### Logical And

まず左の式を評価し，左の式が `0` 以外のときのみ右の式を評価します．どちらも `0` ではないときは `1` と評価され，それ以外は `0` と評価されます．
[if-elif-else文](../if.html)や[loop文](../loop.html)と組み合わせて使うと便利です．

```
a: 3
b: 10
c: a < 4 && b > 10
```

`c` には `0` が代入されます．

### <lord-icon src="https://cdn.lordicon.com/giaigwkd.json" trigger="loop" delay="1000" style="height:2em"></lord-icon>Bitwise Or

<small>この機能は開発中です</small>

### <lord-icon src="https://cdn.lordicon.com/giaigwkd.json" trigger="loop" delay="1000" style="height:2em"></lord-icon>Bitwise Xor

<small>この機能は開発中です</small>

### <lord-icon src="https://cdn.lordicon.com/giaigwkd.json" trigger="loop" delay="1000" style="height:2em"></lord-icon>Bitwise And

<small>この機能は開発中です</small>

### Equality

まず左の式を評価し，続いて右の式を評価します．\\(2\\)つの値が等しいとき `1` と評価され，異なるとき `0` と評価されます．
[if-elif-else文](../if.html)や[loop文](../loop.html)と組み合わせて使うと便利です．

```
a: 3
b: a = 3
```

`b` には `1` が代入されます．

```
a: 3
b: a != 3
```

`b` には `0` が代入されます．

### Relational

まず左の式を評価し，続いて右の式を評価します．\\(2\\)つの値の大小関係に基づいて， `1` または `0` と評価されます．
[if-elif-else文](../if.html)や[loop文](../loop.html)と組み合わせて使うと便利です．

```
a: 3
b: a < 3
```

`b` には `0` が代入されます．

```
a: 3
b: a <= 3
```

`b` には `1` が代入されます．

```
a: 3
b: a > 3
```

`b` には `0` が代入されます．

```
a: 3
b: a >= 3
```

`b` には `1` が代入されます．

### <lord-icon src="https://cdn.lordicon.com/giaigwkd.json" trigger="loop" delay="1000" style="height:2em"></lord-icon>Shift

<small>この機能は開発中です</small>

### Additive

和は `+` ，差は `-` で行います．

```
a: 10
b: 20
c: a + b - 200
```

`c` には `-170` が代入されます．

### Multiplicative

積は `*` ，商は `/` で行います．剰余は `%` です．

```
a: 10 / 5
```

`a` には `2` が代入されます．

```
a: 10
b: 3
c: a % b
```

`c` には `1` が代入されます．

```
a: 12
b: a * 200
```

`b` には `2400` が代入されます．
