## 文档内命名规则
* 自定变量名 用驼峰法，第一个首字母小写，其余部分首字母大写,矮驼峰法.
* 自定函数名 全部首字母皆大写.
* 英文半角标点符号后需要加一个空格, 且当有括号时, 括号内每个字符内都要加空格
    >vscode启用了拓展"中文标点符号转英文",所以不需要麻烦地来回切换输入法来在中文模式下使用markdown语法.
* 按照惯例, typedef定义的新类型名需要全大写, 如果需要隐藏指针, 那么最后加上下滑线_(指针变量不需要加! 类型名才要加). struct类型名全大写, 变量名驼峰法
* 库声明命名  _库_H
* 宏定义 _全部大写加两边下划线_
    (注:　虽然全大写命名很麻烦,　但是vscode是支持小写也能补全大写的啦)
    全大写时, 不同词义间用_隔开.

## 代码书写规范( 适用c )
1. 函数名之后不要留空格，紧跟左括号,  以与关键字区别。
2. 像 if、 for、 while 等关键字之后应留一个空格再跟左括号，以突出关键字。
3. ‘，’之后要留空格。在 for 语句中的分号之后要留空格，如 for (i=0; i<5; i++)
4. 对于表达式比较长的 for 语句和 if 语句，为了紧凑起见可以适当地去掉一些空格。
5. 赋值操作符、比较操作符、算术操作符、逻辑操作符、位域操作符，如:“ =”、“ +=” “>=”、“ <=”、“ +”、“ *”、“ %”、“ &&”、“ <<”、 “ ^”等二元操作符的前后应当加空格。
6. 一元操作符如“ !”、“ ~”、“ ++”、“ --”、“ &”（地址运算符）等前后不加空格。
