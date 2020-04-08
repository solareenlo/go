# interface
- method の一覧を定義する型．
- 型に method を実装することによって，interface を実装する．
- interface を明示的に宣言する必要はない．
- この定義と実装を切り離していることを暗黙のインターフェースという．
  - interface をこのような実装にした理由の1つは，同じインターフェースを実装する異なる構造体を，新たな型として定義できるから．

# interface value
- インターフェースの値は，下のような値と具体的な型のタプルのように考えることができる．
    ```bash
    (value, type)
    ```
- インターフェースの値は，特定の基底になる具体的な型の値を保持する．
- インターフェースの値のメソッドを呼び出すと，その基底型の同じ名前のメソッドが実行される．
- インターフェース自体の中にある具体的な値が nil の場合，メソッドは nil をレシーバーとして呼び出される．
  - 具体的な値として nil を保持するインターフェースの値それ自体は非 nil である．

## nil interface
- nil interface の値は，値も具体的な型も保持しない．
  - nil interface には呼び出す具体的なメソッドを示す型がタプル内に存在しないため，nil interface のメソッドを呼び出すと，ランタイムエラーになる．

## empty interface
- empty interface は0個のメソッドを指定されたインターフェースのこと．
 - empty interface は，任意のかたの値を保持できる．
 - 全ての型は，少なくとも0個のメソッドを実装している．

## type assertion
- type assersion は，interface の値の基になる具体的な値を利用する手段を提供する．
    ```go
    t := i.(T)
    ```
  - 上の文は，interface の値 i が具体的な型 T を保持し，基になる型 T の値を変数 t に代入することを主張する．
  - i が T を保持していない場合，上の文は panic を引き起こす．
- interface の値が特定の型を保持しているかどうかをテストするために，type assersion は2つの値を返すことができる．
  - 2つの値とは，基になる値とアサーションが成功したかどうかを報告するブール値．
  ```go
  t, ok := i.(T)
  ```
  - i が T を保持していれば，t は基になる値になり，ok は true になる．
  - そうでなければ，t は型 T のゼロ値になり，ok は false になる．この時は panic は起きない．

## type switch
- type switch はいくつかの type assersion を直列に使用できる構造になっている．
- type swithc の case は型を指定し，type switch の値は指定された interface の値が保持する値の型と比較される．
