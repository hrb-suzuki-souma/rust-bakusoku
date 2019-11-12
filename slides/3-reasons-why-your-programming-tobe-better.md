# ここで質問です

---

# Q. あなたが考える「プログラミングでする上で大事なこと」を３つ教えてください

---

# 答え
### 1. 型
### 2. 型
### 3. 型

---

# 我々の目標
型を書いたらなぜかアプリが動くみたいにしたい

---

# ということは…
型をいい感じにかける言語 = 良い言語*   

---
   
#### * 諸説あります

---

# 簡単に最強の型を手に入れる方法

---

# すごいH本を読んでください

<img src="../img/sugoi-h.jpg" />

---

# 型で大事なポイント
- 型で現実のモノ、コトを正しく表現できること
  - 列挙型
  - 直和型
  - **直積型**
- 型で言語機能を拡張できること
  - **型クラス**
- 型によって秩序を作り出せること
  - **パターンマッチ**
  - 型境界

などなど

---

# 直積型？🤔
代数的データ型とも言います   

```rust
enum HttpError {
    NotFound,
    BadRequest(String),
    Unauthorized,
    InternalServerError(String),
}
```

`BadRequest` と `InternalServerError` の時だけ併せてその理由 `String` を持たせることができる

---

# 型クラス？🤔
*型クラス* はHaskellの用語   
Rustでは *Trait* と呼びます   
多言語で言うところの `interface` みたいなものです

```rust
struct UserName {
    firstName: String
    lastName: String
}

trait ToString {
    pub fn to_string(&self) -> String
}

// 実装はこんな感じでする
impl ToString for UserName {
    fn to_string(&self) -> String {
        format!("{} {}", self.firstName, self.lastName)
    }
}
```
 
