# slice
- 可変長配列を持たない代わりに実装された型．
- 配列全体のポインタ（`ptr`），配列の長さ（`len`），配列の容量（`cap`）を保持するデータ構造．
- 配列の部分列を簡単に取り出せる．

# 公式による解説ブログ
- [Go Slices: usage and internals](https://blog.golang.org/slices-intro)

# slice と array の定義
## slice の定義
```go
test := []int{1, 2, 3}    //要素数3 容量3の slice
test := make([]int, 3, 3) //要素数3 要素数3の slice
```

## array の定義
```go
var test[]                //要素数0  容量0の array
var test[10]              //要素数10 容量10の array
test := [3]int{1, 2, 3}   //要素数3  容量3の array
test := [...]int{1, 2, 3} //要素数3  容量3の array
```

- Reference: [Go言語のスライスで勘違いしやすいこところ](https://qiita.com/Kashiwara/items/e621a4ad8ec00974f025)
