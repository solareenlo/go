# closure とは
- 関数オブジェクトの1つ．
- 引数以外の変数を実行時の環境ではなく，closure が定義されている環境（静的スコープ）において解決することを特徴とする．

# closure のメリット
- closure を高階関数の引数に渡して，記述の簡素化や高階関数の外側の状態の参照が可能になる．
- closure は遅延評価される（呼び出されるまで何も実行しない）ので，制御構造の定義に用いることができる．

# Go の関数は closure
- closure は closure 自身の外部から変数を参照する関数値のことであり，
- closure は参照された変数へアクセスして変えることができる．
- その意味で，closure はその変数へ bind されている．

# Go における closure としての無名関数の特徴
- closure から参照されたローカル変数は，関数内のローカル変数とは別物になりclosure の変数になる．
- closure が何らかの形で参照される限り closure の変数も破棄されない．