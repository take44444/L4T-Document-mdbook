<script src="https://cdn.lordicon.com/xdjxvujz.js"></script>

# 配列

`array` 型では，任意の同じ型の値を複数扱うことができます．

例えば， `num` 型の配列は，以下のように扱うことができます．

```
array<num>[3] a, b
b[2]: 300
a[0]: 10
a[1]: 20
a[2]: a[0] + a[1]
b: a
b[0]: 100
b[1]: a[0] + a[1] - b[0]
```

上のコードでは，最終的に配列 `a` の値は `10` ， `20` ， `30` となり，配列 `b` の値は `100` ， `-70` ， `30` となります．( `b[2]` の値は2行目で `300` になりますが，6行目で `30` に上書きされます．)

```admonish warning title="Caution!"
6行目で `b` に `a` を代入した後，7行目で `b[0]: 100` としていますが，**この時 `a[0]` の値は変化しません**．配列同士での代入演算では，**deep copy**が行われます．
```

他にも，配列の配列(\\(n\\)次元配列)や[構造体](./struct.html)の配列，[ポインタ](./ptr.html)の配列も扱うことができます．

以下は\\(2\\)次元配列の例です．

```
array<array<num>[2]>[3] a, c
array<num>[2] b
a[0][0]: 100
a[0][1]: 200
a[1][0]: 300
a[1][1]: 400
b: a[1]
b[1]: 4000
a[2]: b
c: a
```

このコードの7行目や9行目，10行目でも同様に**deep copy**が行われます．
