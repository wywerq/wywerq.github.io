## 变量

声明
`Dim 变量名 As 数据类型`
`Dim 数组名(a,b) As 数据类型`

| 数据类型 | 描述         |
| -------- | ------------ |
| Boolean  | 布尔型       |
| Data     | 日期与时间型 |
| Double   | 双浮点型     |
| Integer  | 整数型       |
| Long     | 长整数型     |
| String   | 字符串型     |
| Variant  | 万能型       |

## 运算符

| 符号 | 作用     |
| ---- | -------- |
| ^    | 取次幂值 |
| \    | 整除     |
| MOD  | 取余     |

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

### 取范围随机数

[min, max]

`Int((max - min + 1) * rnd + min)`

### 字符串

| 函数功能         | 语法格式                       | 参数说明                                                                                              |
| ---------------- | ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| 从左侧提取字符   | `Left(String, Length) `        | `Length`：要提取的字符数量                                                                            |
| 从中间提取字符   | `Mid(String, Start[, Length])` | `start`：提取的起始位置<br>`Length`：可选，要提取的字符数；省略则返回从起始位置到字符串末尾的所有字符 |
| 从右侧提取字符   | `Right(String, Length)  `      | `Length`：要提取的字符数量                                                                            |
| 删除字符两端空格 | `Trim(String)`                 |
| 小写转大写       | `UCase(String)`                |                                                                                                       |
| 大写转小写       | `LCase(String)`                |                                                                                                       |
