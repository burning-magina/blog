---
layout: post
title: javascript中正则表达式学习
categories: javascript
description: javascript中正则表达式学习
keywords: javascript,正则表达式
---

## 定义

- 通过构造函数

``` javascript
var reg =new RegExp("\\?(\\w{1,}=\\w{1,}&){1,}\\w{1,}=\\w{1,}");
```

**注意：**

    1. 使用构造函数定义正则表达式，注意大小写，否则就会不起作用。
    2. 特殊字符就需要使用\进行转义。javascript中特殊字符如下：
	
        * . ? + $ ^ [ ] ( ) { } | \ / 

--------

 - 通过2个斜杠 //

``` javascript
var date = /^(\d{1,4})(-|\/)(\d{1,2})(-|\/)(\d{1,2})$/;
```

## 学习

在我们的代码中，使用最多的都是匹配字符串类型的，所以经常使用^和$符号：

|符号|含义|
|:---:|:---:|
| ^ | 匹配字符串的开始|
| $ | 匹配字符串的结束 |

常用的元字符：

|代码|说明|
|:---:|:---:|
| . | 匹配除换行符以外的任意字符|
| \w | 匹配字母或数字或下划线或汉字|
| \s | 匹配任意的空白符 |
| \d | 匹配数字 |
| \b | 匹配单词的开始或结束 |

常用的限定符：

|代码|说明|
|:---:|:---:|
| * | 重复零次或更多次|
| + | 重复一次或更多次|
| ? | 重复零次或一次 |
| {n} | 重复n次 |
| {n,} | 重复n次或更多次 |
| {n,m} | 重复n到m次 |
|()|标记一个子表达式的开始和结束位置|
|[]|标记一个中括号表达式的开始|
|{ }|标记限定符表达式的开始|
| \|| 指明两项之间的一个选择。要匹配 \|，请使用 \\\| |

常用的反义代码:

|代码|说明|
|:---:|:---:|
| \W | 匹配任意不是字母，数字，下划线，汉字的字符|
| \S | 匹配任意不是空白符的字符|
| \D | 匹配任意非数字的字符 |
| \B | 匹配不是单词开头或结束的位置 |
| [^x] | 匹配除了x以外的任意字符 |
| [^aeiou] | 匹配除了aeiou这几个字母以外的任意字符 |

其他：

|代码|说明|
|:---:|:---:|
| \a | 报警字符(打印它的效果是电脑嘀一声)|
| \b | 通常是单词分界位置，但如果在字符类里使用代表退格|
| \t | 制表符，Tab |
| \r | 回车 |
| \v | 竖向制表符 |
| \f | 换页符 |
| \n | 换行符 |
| \e | Escape |
| \0nn | ASCII代码中八进制代码为nn的字符|
| \xnn | ASCII代码中十六进制代码为nn的字符 |
| \unnnn | Unicode代码中十六进制代码为nnnn的字符 |
| \cN | ASCII控制字符。比如\cC代表Ctrl+C |
| \A | 字符串开头(类似^，但不受处理多行选项的影响) |
| \Z | 字符串结尾或行尾(不受处理多行选项的影响) |
| \z | 字符串结尾(类似$，但不受处理多行选项的影响) |
| \G | 当前搜索的开头 |

还有其他的表达式有需要的可以自己搜索,比如断言等。

## 举例

1. 校验基本日期格式
    >(1-4位数字) + (/或者\|) + (1-2位数字) + (/或者\|) + (1-2位数字)

    ``` javascript
    var reg = /^(\d{1,4})(-|\/)(\d{1,2})(-|\/)(\d{1,2})$/;
    reg.lastIndex = 0;//调试函数test（）专属用句，不然你会怀疑正则表达式的能力
    reg.test('1999-02-30');
    reg.test('1-1-1');
    reg.test('1-1/1');
    
    ```

2. 校验密码长度
    >包含大小写字母和数字的组合，不能使用特殊字符，长度在8-10之间

    ``` javascript
    var reg = /^(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,10}$/;
    ```
    
    解释一下：比如：/(abc)(?=\d)/；表示零宽度正先行断言，匹配字符串中abc后面是数字的所有abc组合；本例子中表示：字符串中必须包含大小写字母和数字的组合并且字符串的长度在8到10位之间。
    >[关于断言的学习](https://www.cnblogs.com/leezhxing/p/4333773.html)。
    
3. 校验金额
    >金额校验，精确到2位小数。

    ``` javascript
    var reg = /^[0-9]+(\.[0-9]{2})?$/;
    ```
    
4. 校验中文
    >字符串只能是中文

    ``` javascript
    var reg = /^[\u4e00-\u9fa5]*$/
    ```
    
5. Email 地址
    >如题

    ``` javascript
    var reg = /^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/
    ```
    
6. [常用的正则表达式](http://www.jqhtml.com/6227.html)