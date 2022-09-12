<script src="https://cdn.lordicon.com/xdjxvujz.js"></script>

# 構造体

`array` 型では同じ型の複数の値を扱うことができましたが，`struct` 型では，違う型も含み得る複数の値を扱うことができます．

構造体の宣言は，以下のように書きます．

```
struct A
  num x
  array<num>[2] arr

struct B
  num x
  ptr<array<num>[2]> arrp
  struct A a
  ptr<struct B> other

```

これで，構造体 `A` ，構造体 `B` という2つの型が使えるようになりました．以下のようにして，構造体構造体 `A` ，構造体 `B` の型の変数を定義し，使うことができます．

```
array<num>[2] arr
struct A a
struct B b1, b2

arr[0]: 300
arr[1]: 400

a.x: 10
a.arr[0]: 100
a.arr[1]: 200

a.arr: arr

b1.x: a.x: 100
b1.arrp: &a.arr
b1.a: a
b1.other: &b2
b2: b1
b2.other: &b1
(*(*(*b1.other).other).arrp)[0]: 500
```

`.` を用いて，構造体のメンバにアクセスすることができます．

```admonish warning title="Caution!"
18行目で `b2` に `b1` を代入した後，19行目で `b2.other: &b1` としていますが，**この時 `b1.other` の値は変化しません**．構造体同士での代入演算では，**deep copy**が行われます．
```

## 構造体のサイズについて考える

L4Tでは，構造体のサイズはコンパイル時に決定できる必要があります．以下の構造体の宣言を見てください．

```
struct A
  num x
  struct A other

```

もちろん構造体のメンバに構造体の実体を持つことはL4Tでも許可されていますが，上のコードは正しくありません．<a href="http://35.247.86.97/" target="_blank"><u>**L4T Playground**</u></a>で上の構造体をコンパイルして，下のようなエラーが出ることを確認してみましょう！

```
line:3/pos:10: cannot determine size of struct A
  struct A other
         ^
```

これは，構造体 `A` のサイズを決定できないというエラーです．ここで構造体 `A` のサイズを考えてみましょう．構造体 `A` のサイズは，

$$\rm{sizeof}(A) = 8 + \rm{sizeof}(A)$$

となり，右式に再び\\(\rm{sizeof}(A)\\)が出てきてしまうため，構造体 `A` のサイズを計算することができないわけです．

同様に，以下のようなコードもコンパイルされません．(<a href="http://35.247.86.97/" target="_blank"><u>**L4T Playground**</u></a>で試してみましょう！)

```
struct A
  num x
  struct B b

struct B
  array<struct C>[3] c

struct C
  struct A a

```

$$\rm{sizeof}(A) = 8 + \rm{sizeof}(B)$$
$$\rm{sizeof}(B) = 3 \times \rm{sizeof}(C)$$
$$\rm{sizeof}(C) = \rm{sizeof}(A)$$

であるため，
$$\rm{sizeof}(A) = 8 + 3 \times \rm{sizeof}(A)$$
となります．

しかし，以下のようなコードは正しいコードです．

```
struct A
  num x
  ptr<struct A> other

```

`ptr<struct A>` は[ポインタ](./ptr.html)であり，構造体 `A` のサイズに依らず8バイトだからです．
