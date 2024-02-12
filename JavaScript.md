# Javascript 筆記 - For Frontend

> Javascript 功能：增強網頁的動態效果和互動性

## 目錄

> :::spoiler 清單
> [TOC]
> :::

---

### 基本 function

- console.log()
  > 將 message 輸出到 web 主控台
  > message 可以是 string 或多個 JS Object
  ```json
  //snippets
  "console": {
    "prefix": "con",
    "body": ["console.log()"],
    "description": "console"
  }
  ```
- window.alert()
  > 顯示可選消息的對話框，並等待 user 關閉對話框
- window.prompt()
  > 顯示可選消息的對話框，但提供文字輸入框，並等待 user 輸入或取消對話框

### Lexical Structure

> 程式語言的文法結構規則，如關鍵字、變數名稱、運算符 etc.

- Case Sensitive (區分大小寫)
  > 在 JS 中，大小寫是有差別的
- Minification
  > 一種縮小程式碼檔案大小的技術
  > 伺服器上的 JS code 都會被刪除空白鍵、換行鍵
- Comment out
  > 單行為 //
  > 多行為 /\* \*/
- 變數命名
  > 開頭需要用文字、underscore(\_)、dollar sign($)為開頭
  > 不能用數字開頭
- 保留字
  > 包含：null, of, if, then, in, finally, for, while, break, continue, switch, try, let, const, var, etc.
- Unicode
  > JS 使用 Unicode 字元集，String 內可由任何 Unicode 組成
- Semicolons(;)
  > 可用來分隔程式語句
  > 為 optional (可用可不用)

### Variable & Assignment

- let
  > 宣告變數 (值可改變)
- const
  > 宣告常數 (值不可變)
- ❌var
  > 古老語法，現不要使用 var 宣告變數

> let 若宣告時無 initialization(賦予初始值)，則 value 為 undefined

> 用 const 宣告常數需要馬上 initialization

> let 跟 const 都不能重複賦值 (reassignment is not allowed)

> JS Engine 中存在 GC (Garbage Collector)，會監控並刪除已經無用的 object

### Data Type

- primitive
  > 基本數據類型
  > 不是 object，不具有 properties 和 method
  - Number
    > 整數與小數
    - operator (運算子)
      > `+` `-` `*` `/` > `%` mod、remainder operator(餘數)
      > `**` exponentiation operator(指數)
      > `+=` `-=` `*=` `/=` > `++` `--`
    - Methods
      - toString()
        > return 一個 number 的 string
      - toFixed(n)
        > return 一個 number 到小數後第 n 位的 String
        ```javascript
        let num = 3.14159;
        let result = num.toFixed(2);
        console.log(result); // "3.14"
        ```
        > 由於二進制不能精確表示所有小數，因此 0.1 + 0.2 === 0.3 會 return false
  - BigInt
    > 任意長度的整數
  - String
    > 字串符
    > 在 JS 中，可以使用 single or double quotation mark( ''或"" )，只有單雙混用時要注意夾層拆分
    > 使用 `\n`可以換行
    > string 之間`+` 連接，稱作 concatenation
    > string 之間不能進行其他 operator，如`-` `*` `/`，會出現 NaN(Not a Number)
    > ℹ️ 若 String 跟 Number 之間使用 `+`，會自動轉為兩個 string 做 concatenation
    - Attributes & Methods
      - length
        > return string 的長度
      - [n]
        > return index 為 n，即第 n 個字 (從 0 開始)
      - slice(indexStart[,indexEnd])
        > 提取 string 的一部份作為新 string 並 return，不修改原本的 string
        > indexStart -> inclusive (包含的)
        > indexEnd -> (不包含的)
        ```javascript
        let str = "Javascript";
        str.slice(1, 5); 
        ```
      - indexOf(substring)
        > return substring 的 index，若找不到 substring 會 return -1
        ```javascript
        let str = "Javascript";
        console.log(str.indexOf("s")); // 4
        console.log(str.indexOf("vas")); // 2
        console.log(str.indexOf("z")); // -1
        ```
      - toUpperCase()
        > return 轉換大寫的 string
      - toLowerCase()
        > return 轉換小寫的 string
      - split(pattern)
        > 接受 pattern (格式)，搜索後將 string 轉為有序 array，並 return 該 array  
        > patter 可以是 regular expression
        ```js
        let str = "Today is a good day.";
        let result = str.split(" ");
        console.log(result);
        //Array(5) ["Today", "is", "a", "good", "day."]
        ```
      - startWith(substring)
        > 檢測 string 是否以 substring 開頭
      - endsWith(substring)
        > 檢測 string 是否以 substring 結尾
      - includes(substring)
        > 檢測 string 是否包含 substring
      - charCodeAt(n)
        > return string 的 index 為 n 的 UTF-16 code unit (介於 0~65535)
  - Boolean
    > 布林值，true/false 二元型態
    > 使用 Unary operator 的 `!` 可以反轉 true/false
    > 使用 Unary operator 的 typeof() 可以用來確認資料型別
  - null
    > 代表某個故意不存在的值
    > 意義為 has nothing inside
  - undefined
    > 沒有 assignment 變數的 value
    > 意義為 waiting for assignment
    > function 的預設 value
  - symbol
    > unique identifier (唯一標識符)
- non-primitive
  - object
    > 物件，一種抽象的概念，指獨立、具有狀態和行為的實體，包含 properties 和 methods
    > JS 中的 object 泛指 array、object、function etc.

### Operators

- assignment
  > `=`
- comparison
  > operand(運算元)為兩個任意 data type 且運算結果為 bool
  - `==`
    > 若兩運算子相等，回傳 true
    > return true if the operands are equal
  - `!=`
    > 若兩運算子不相等，回傳 true
    > return true if the operands are not equal
  - `===`
    > 若兩運算子相等，型別也相同，回傳 true
    > return true if the operands are equal and of the same data type
  - `!==`
    > 若兩運算子不相等或型別不同，回傳 true
    > return true if the operands are of different type or not equal
  ```javascript
  console.log(3 == "3"); // true
  console.log(3 === "3"); // false
  console.log(3 != 2); // true
  console.log(3 !== "3"); // true
  ```
  - `>`
  - `>=`
  - `<`
  - `<=`
- logical
  > operand(運算元)為兩個任意 data type 且運算結果為 bool
  - `&&`
    > AND 邏輯
  - `||`
    > OR 邏輯
- typeof (unary)
- negation (unary)
  > `!`
- increment (unary)
  > `++` `--`
- bitwise
- arithmetic
  > `+` `-` `*` `/` etc.

### 非同步

#### Promise

使用 Promise 搭配 Async/Await 發送多個 API 技巧

```javascript
const promises = [
  axios.get("https://vue-lessons-api.vercel.app/photo/list"),
  axios.get("https://vue-lessons-api.vercel.app/seo/home"),
  axios.get("https://vue-lessons-api.vercel.app/city/list"),
  axios.get("https://vue-lessons-api.vercel.app/photo/list?status=error"), // -> 這個會發生錯誤
];

// 遇到錯誤就會停止，進到catch
const promiseAll = async () => {
  try {
    const res = await Promise.all(promises);
    console.log(res);
  } catch (err) {
    console.err("ERROR=>", err.response.data);
  }
};

// 遇到錯誤不會停止，會跑完之後統一進到res的array，標記哪些成功、哪些失敗
const promiseAllSettled = async () => {
  try {
    const res = await Promise.allSettled(promises);
    console.log(res);
  } catch (err) {
    console.log(err);
  }
};
```

### 英文名詞定義

- assign
  > 將一個物件的屬性複製到另一個物件
- assignment
  > 賦值的操作
- attribute
  > 屬性，用於 HTML 標記，需要解析跟重新渲染才能修改
- concatenation
  > string 之間的串接
- initialization
  > 為變數、常數、屬性等資料結構賦予一個初始值的行為
- initializer
  > 變數、常數、屬性等的初始值
- object
  物件(繁中) 或 對象(簡中)
  > 一種抽象的概念，指獨立、具有狀態和行為的實體，包含屬性值 (properties)和方法 (methods)
- operand
  > 運算元
- pattern

  > HTML 用於指定 form 輸入格式的正則表達式

- property
  > 屬性值，可以直接在 JS 進行存取跟修改
- unary
  > 單一的

---

###### tags: `Front-end` `JavaScript`

{%hackmd HJRke1a33 %}
