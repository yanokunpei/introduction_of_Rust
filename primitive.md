# プリミティブ型
---

## 数値型
Rustの数値型は
- i8
- i16
- i32
- i64
- u8
- u16
- u32
- u64
- f32
- f64
- isize
- usize  

があります。  
左のアルファベット一文字は
- i : 符号あり整数型(int)
- u : 符号なし整数型(unsigned int)
- f : 浮動小数点型(float, double)

を表します。
右の数値はbit数です。  
isize,usizeのbit数は実行しているマシンのポインタのサイズに依存します。
```Rust
let x = 1; //i32
let y = 1.0; //f64
```
---
## char
char型はユニコードのスカラ値です。つまりRustのchar は4バイトです。  
 char はシングルクオート（ ' ）で囲います。
```Rust
let x = 'x';
let two_hearts = '💕';
```
---
## bool
いつものboolean型
```Rust
let x: bool = true;
let y = false;
```
---

## 配列
固定長の同じ型の要素のリスト。 デフォルトではイミュータブル。
```Rust
let x = [1, 2, 3]; // [i32; 3]
let mut y = [1, 2, 3]; // [i32; 3]
```
配列は [T; N] という型を持ちます。
Tは中身の要素の型、N は配列の長さです。  
配列の要素は0から始まり、配列の長さは x.len() で求められます。
```Rust
let x =[2,4,8,16,32];
println!("{}", x[0];     // 2
println!("{}", x[2];     // 8
println!("{}", x.len()); // 5
```
配列の各要素を同じ値で初期化するための省略表現があります。 この例では、 x の各要素は 0 で初期化されます。
```Rust
let x = [0; 10]; // a: [i32; 10]
```
---

## スライス  
スライスは他のデータ構造の参照(またはビュー)です
コピーすることなく配列の要素へ安全に効率的にアクセスするのに便利です。スライスは直接作られるのではなく既存の変数から作られます。スライスは定義された長さを持ちミュータブルにもイミュータブルにもできます。
スライスは型&[T]を持ちます。
スライスを作るのには`&`と`[]`を使います。
`&`はスライスが参照先と同じであることを示し`[]`はレンジを示しスライスの長さを定義します。
```Rust
let x = [0,1,2,3,4,5];
let slice1 = &x[..];    //xのすべての要素を持つスライス
let slice2 = &x[1..4];  //x[1]からx[4]までの要素を持つスライス
```
---
## &str型
 &str は「文字列のスライス」と呼ばれます。 文字列のスライスは更不可能な固定のサイズを持ち、UTF-8のバイトシーケンスへの参照です。
 ```Rust
 let hello = "hello  world"; // &'static str
 ```
 ---

## タプル
タプルは固定サイズの順序ありリストです。
```Rust
let x = (1, "hello");　// (i32, &str)
let (x, y, z) = (1, 2, 3);
println!("{}", x); // 1
```
let の左辺にはパターンを書くことができ、右辺とマッチしたら、複数の束縛を一度に割り当てることができます。この場合、 let がタプルを要素を3つの変数に割り当てます。  
`,`を付けることで要素1のタプルを丸括弧の中の値と混同しないように明示することができます。  
```
 (0,); // 1要素のタプル  
 (0); // 丸括弧に囲まれたゼロ
```
タプルのフィールドにはインデックス構文でアクセスすることもできます。
```Rust
let x = (1, 2, 3);
println!("{}", x.0); // 1
println!("{}", x.1); // 2
println!("{}", x.2); // 3
```  
配列のインデックスと同じように、0から始まります。しかし、配列のインデックスと異なり`[]`ではなく `.` を使います。

---
## 関数
関数も型を持ちます。
```Rust
fn func(x: i32) -> i32 { println!("xxx"); }
let x: fn(i32) -> i32 = func;
```
この場合、 x は i32 を受け取り i32 を戻す関数への「関数ポインタ」です。