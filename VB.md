## 小芝士 - 代码补全

- 显示代码提示：`Ctrl+J`
- 补全代码：`Tab`

示例：  
输入`R` -> `Ctrl+J`显示代码提示 -> 上下方向键选择代码 -> 按`Tab`键补全

## 变量

### 声明

`Dim 变量名 As 数据类型`  
`Dim 数组名(上界) As 数据类型` 数组范围：[0,上界]  
`Dim 数组名(下界 to 上界) As 数据类型` 数组范围：[下界,上界]

### 数据类型

| 数据类型  | 描述       |
| --------- | ---------- |
| `Boolean` | 布尔型     |
| `Data`    | 时间日期型 |
| `Double`  | 双浮点型   |
| `Integer` | 整数型     |
| `Long`    | 长整数型   |
| `String`  | 字符串型   |
| `Variant` | 万能型     |

## 常量

| 名称   | 描述                      |
| ------ | ------------------------- |
| 换行符 | `vbCrLf`                  |
| Tab    | `vbTab`                   |
| 颜色   | `vbRed,vbGreen,vbBlue...` |

## 运算符

| 符号  | 作用                |
| ----- | ------------------- |
| `^`   | 取次幂值            |
| `\`   | 整除，优先级高于MOD |
| `MOD` | 取余                |

为避免优先级问题，可以用括号()包裹表达式

## 结构

### 条件语句

```vb
If 条件1 Then

ElseIf 条件2 Then

Else

End If
```

```vb
Select Case 变量
    Case 值
          代码
End Select
```

### 循环语句

```vb
For i = 1 To 10 Step 1

Next
```

```vb
Do {While|Until} 条件

Loop

Do

Loop {While|Until} 条件
```

```vb
While 条件

end While
```

## 函数

| 函数功能     | 语法格式      | 参数说明 |
| ------------ | ------------- | -------- |
| 字符串转ANSI | `Asc(String)` |
| ANSI转字符串 | `Chr(ANSI码)` |

### 数学

| 函数功能               | 语法格式                           | 说明                                                                            |
| ---------------------- | ---------------------------------- | ------------------------------------------------------------------------------- |
| 字符串转数值           | `Val(String)`                      | 从左往右依次取出数值，如果碰到非数值则停止                                      |
| 取整                   | `Int(Number)`                      | 正数去掉小数点后面的数字，负数取偏小的整数。如-1.25取的是-2，如-98.9取的是-99。 |
| 随机数                 | `Rnd`                              | 区间：[0, 1)                                                                    |
| 初始化随机数生成器种子 | `Randomize`                        |
| 取范围随机数           | `Int((max - min + 1) * Rnd + min)` | `min`：最小值<br>`max`：最大值<br>区间：[`min`, `max`]                          |

### 字符串

| 函数功能         | 语法格式                       | 参数说明                                                                                              |
| ---------------- | ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| 从左侧提取字符   | `Left(String, Length) `        | `Length`：要提取的字符数量                                                                            |
| 从中间提取字符   | `Mid(String, Start[, Length])` | `Start`：提取的起始位置<br>`Length`：可选，要提取的字符数；省略则返回从起始位置到字符串末尾的所有字符 |
| 从右侧提取字符   | `Right(String, Length)  `      | `Length`：要提取的字符数量                                                                            |
| 删除字符两端空格 | `Trim(String)`                 |
| 小写转大写       | `UCase(String)`                |                                                                                                       |
| 大写转小写       | `LCase(String)`                |                                                                                                       |

### 时间日期

| 函数功能     | 语法格式                         | 说明                                                                                                                                                                                                                                      |
| ------------ | -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 取日期       | `Date`                           | 返回值如：`2026/3/17`                                                                                                                                                                                                                     |
| 取日期与时间 | `Now`                            | 返回值如：`2026/3/17 13:00:00`                                                                                                                                                                                                            |
| 取年份       | `Year(Date)`                     | 取当前年份示例：`Year(Date)` `Year(Now)`                                                                                                                                                                                                  |
| 取月份       | `Month(Date)`                    |
| 取星期       | `Weekday(Date)`                  |
| 取天数       | `Day(Date)`                      |
| 取小时       | `Hour(Time)`                     | 取当前小时示例：`Hour(Now)`                                                                                                                                                                                                               |
| 取分钟       | `Minute(Time)`                   |
| 取秒钟       | `Second(Time)`                   |
| 格式化       | `Format(Expression,)`            |
| 增加时间间隔 | `DateAdd(Interval,Number,Date)`  | `Interval`：单位<br>如：<br> yyyy - 年<br>q - 季度<br>m - 月<br>y - 当年的第几天<br>d - 日<br>w - 当周的第几天<br>ww - 周<br>h - 小时<br>n - 分钟<br>s - 秒<br>`number`：要增加的单位数<br><br>取一小时后时间示例：`DateAdd("h", 1, Now)` |
| 取时间间隔   | `DateDiff(Interval,Date1,Date2)` |                                                                                                                                                                                                                                           |

## 算法

`a`：数组  
`Length`：数组长度
`c`：临时变量

### 冒泡排序

```vb
For i = 1 To Length
    For j = 1 To Length - i
        If a(j) > a(j + 1) Then
            c = a(j)
            a(j) = a(j + 1)
            a(j + 1) = c
        End If
    Next
Next
```

![](https://www.runoob.com/wp-content/uploads/2019/03/bubbleSort.gif)

### 选择排序

`min`：最小值的下标

```vb
For i = 1 To Length
    min = i
    For j = i + 1 To Length
        If a(j) < a(min) Then min = j
    Next
    c = a(i)
    a(i) = a(min)
    a(min) = c

Next
```

![](https://www.runoob.com/wp-content/uploads/2019/03/selectionSort.gif)

### 插入排序/直接排序

![](https://www.runoob.com/wp-content/uploads/2019/03/insertionSort.gif)
