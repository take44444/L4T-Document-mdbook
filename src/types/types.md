<script src="https://cdn.lordicon.com/xdjxvujz.js"></script>

# 型

L4Tの全ての値には型があります．例えば `num a` と宣言した変数 `a` や， `1234` というような値は `num` 型です．L4Tでは，同じ型同士でしか演算ができず，また，ある型として宣言した変数にはその型の値しか代入することができません．この言語仕様により，より**セキュアなコーディングが強制され**，そのおかげで私たちは，実装においてバグを作りにくくなります．

L4Tで扱える型は， [**整数**](/types/num.html)( `num` )，[**配列**](/types/array.html)( `array` )，[**構造体**](/types/struct.html)( `struct` )，[**ポインタ**](/types/ptr.html)( `ptr` )，[**関数ポインタ**](/types/funcptr.html)( `funcptr` )の5つです．