# なぜRustは爆速開発を可能にするのか

---

1. 過不足ない型システム
2. 代替案まで提案してくれるコンパイラ
3. トレートの自動導出

---

1. **過不足ない型システム**
2. 代替案まで提案してくれるコンパイラ
3. トレートの自動導出

---

# Classがない

```rust
struct User {
    pub name: String,
    pub age: i32,
    pub email: String,
}

impl User {
    // static 関数
    pub fn new(name: String, age: i32, email: String) -> Self {
        Self { name, age, email }
    }

    // public 関数
    pub fn validate(&self) -> bool {
        self.validate_name()
    }

    // private 関数
    fn validate_name(&self) -> bool {
        self.name.ne(&"".into())
    }
}
```

---

# 言語レベルのInterface（Trait）

```rust
use std::fmt;

struct Point {
    x: i32
    y: i32
}

impl fmt::Display from Point {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        // ここで (?, ?) の形式で書き出すようにしておく
        write!(f, "({}, {})", self.x, self.y)
    }
}

// 初期化
let origin = Point { x: 0, y: 0 };

println!("The origin is: {}", origin); // -> The origin is: (0, 0)
```

---

# 暗黙の型変換

```rust
pub fn print(str: String) -> () {
    println!("{}", str);
}

pub fn main() -> () {
    // 3はString型ではないが.into()で自動変換される
    print(3.into())
}
```

---

1. 過不足ない型システム
2. **代替案まで提案してくれるコンパイラ**
3. トレートの自動導出

---

# 時間が足りないので実際に書いて確かめてください

---

1. 過不足ない型システム
2. 代替案まで提案してくれるコンパイラ
3. **トレートの自動導出**

---

# .eq()の自動導出

```rust
// derive()を使うと自動導出される
#[derive(Eq)]
struct User {
    name: String
}

let a = User { name: "a".into() }
let b = User { name: "b".into() }

// .eq()関数が自動的に実装されている
a.eq(b)
```
