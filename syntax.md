# 構文
## 命名規約
|対象|書き方|
|:-:|:-:|
|ファイル名|スネークケース|
|変数|スネークケース|
|メソッド|スネークケース|
|構造体|キャメルケース|

## 変数
```Rust
// `_`から始まる変数は`unused`の警告が出ない。  
let _x = 5;

//
let y = &5; // これは`let _y = 5; let y = &_y;` と同じ意味
```
