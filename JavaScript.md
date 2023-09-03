# Javascript筆記 - For Frontend

> Javascript功能：增強網頁的動態效果和互動性

## 目錄
> :::spoiler 清單
> [TOC]
> :::
---
### 基本function
- console.log()
    > 將message輸出到web主控台
    > message可以是string或多個JS Object
    ```json
    //snippets
    "console": {
      "prefix": "con",
      "body": ["console.log()"],
      "description": "console"
    }
    ```
- window.alert()
    > 顯示可選消息的對話框，並等待user關閉對話框
- window.prompt()
    > 顯示可選消息的對話框，但提供文字輸入框，並等待user輸入或取消對話框

### Lexical Structure
> 程式語言的文法結構規則，如關鍵字、變數名稱、運算符 etc.

- Case Sensitive (區分大小寫)
    > 在JS中，大小寫是有差別的
- Minification
    > 一種縮小程式碼檔案大小的技術
    > 伺服器上的JS code都會被刪除空白鍵、換行鍵
- Comment out
    > 單行為 //
    > 多行為 /* */
- 變數命名
    > 開頭需要用文字、underscore(_)、dollar sign($)為開頭
    > 不能用數字開頭
- 保留字
    > 包含：null, of, if, then, in, finally, for, while, break, continue, switch, try, let, const, var, etc.
- Unicode
    > JS使用Unicode字元集，String內可由任何Unicode組成
- Semicolons(;)
    > 可用來分隔程式語句
    > 為optional (可用可不用)

### Variable & Assignment
- let
    > 宣告變數 (值可改變)
- const
    > 宣告常數 (值不可變)
- ❌var
    > 古老語法，現不要使用var宣告變數

> let若宣告時無initialization(賦予初始值)，則value為undefined

> 用const宣告常數需要馬上initialization 

> let跟const都不能重複賦值 (reassignment is not allowed)

> JS Engine中存在GC (Garbage Collector)，會監控並刪除已經無用的object

### Data Type
- primitive
    > 基本數據類型
    > 不是object，不具有properties和method
    - Number
        > 整數與小數
        - operator (運算子)
            > `+` `-` `*` `/` 
            > `%` mod、remainder operator(餘數)
            > `**` exponentiation operator(指數)
            > `+=` `-=` `*=` `/=`
            > `++` `--`
        - Methods
            - toString()
                > return一個number的string
            - toFixed(n)
                > return一個number到小數後第n位的String
                ```javascript
                let num = 3.14159;
                let result = num.toFixed(2);
                console.log(result); // "3.14"
                ```
                > 由於二進制不能精確表示所有小數，因此0.1 + 0.2 === 0.3會return false
    - BigInt
        > 任意長度的整數
    - String
        > 字串符
        
        > 在JS中，可以使用single or double quotation mark( ''或"" )，只有單雙混用時要注意夾層拆分
        
        > 使用 `\n`可以換行
        
        > string之間`+` 連接，稱作concatenation
        > string之間不能進行其他operator，如`-` `*` `/`，會出現NaN(Not a Number)
        
        > ℹ️ 若String跟Number之間使用 `+`，會自動轉為兩個string做concatenation
        - Attributes & Methods
            - length
                > return string的長度
            - [n]
                > return index為n，即第n個字 (從0開始)
            - slice(indexStart[,indexEnd])
                > 提取string的一部份作為新string並return，不修改原本的string
                > indexStart -> inclusive (包含的)
                > indexEnd -> (不包含的)
                ```javascript
                let str = "Javascript";
                str.slice(1,5);// avas
                ```
            - indexOf(substring)
                > return substring的index，若找不到substring會return -1
                ```javascript
                let str = "Javascript";
                console.log(str.indexOf("s")); // 4
                console.log(str.indexOf("vas")); // 2
                console.log(str.indexOf("z")); // -1
                ```
            - toUpperCase()
                > return轉換大寫的string
            - toLowerCase()
                > return轉換小寫的string
            - split(pattern)
                > 接受pattern (格式)，搜索後將string轉為有序array，並return該array   
                > patter可以是regular expression
                ```js
                let str = "Today is a good day.";
                let result = str.split(" ");
                console.log(result);
                //Array(5) ["Today", "is", "a", "good", "day."]
                ```
            - startWith(substring)
                > 檢測string是否以substring開頭
            - endsWith(substring)
                > 檢測string是否以substring結尾
            - includes(substring)
                > 檢測string是否包含substring
            - charCodeAt(n)
                > return string的index為n的UTF-16 code unit (介於0~65535)
    - Boolean
        > 布林值，true/false二元型態
        
        > 使用Unary operator的 `!` 可以反轉true/false
        > 使用Unary operator的 typeof() 可以用來確認資料型別
    - null
        > 代表某個故意不存在的值
        > 意義為has nothing inside
    - undefined
        > 沒有assignment變數的value
        > 意義為waiting for assignment
        
        > function的預設value
    - symbol
        > unique identifier (唯一標識符)
- non-primitive
    - object
        > 物件，一種抽象的概念，指獨立、具有狀態和行為的實體，包含properties和methods
        > JS中的object泛指array、object、function etc.

### Operators
- assignment
    > `=`
- comparison
    > operand(運算元)為兩個任意data type且運算結果為bool
    - `==`
        > 若兩運算子相等，回傳true
        > return true if the operands are equal
    - `!=`
        > 若兩運算子不相等，回傳true
        > return true if the operands are not equal
    - `===`
        > 若兩運算子相等，型別也相同，回傳true
        > return true if the operands are equal and of the same data type
    - `!==`
        > 若兩運算子不相等或型別不同，回傳true
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
    > operand(運算元)為兩個任意data type且運算結果為bool
    - `&&`
        > AND邏輯
    - `||`
        > OR邏輯
- typeof (unary)
- negation (unary)
    > `!`
- increment (unary)
    > `++` `--`
- bitwise
- arithmetic
    > `+` `-` `*` `/` etc.


### 英文名詞定義

- assign
    > 將一個物件的屬性複製到另一個物件
- assignment
    > 賦值的操作
- attribute
    > 屬性，用於HTML標記，需要解析跟重新渲染才能修改
- concatenation
    > string之間的串接
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
    > HTML用於指定form輸入格式的正則表達式

- property
    > 屬性值，可以直接在JS進行存取跟修改
- unary
    > 單一的
    
---
###### tags: `Front-end` `JavaScript`

{%hackmd HJRke1a33 %}