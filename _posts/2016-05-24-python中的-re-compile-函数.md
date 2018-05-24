正则表达式功能十分强大。

“有些人面临一个问题时会想：‘我知道，可以用正则表达式来解决这个问题。’于是现在他们就有两个问题了”——Jamie Zawinski
***
同时正则表达式很难掌握。

正则表达式的各种规则就不在此赘述了，以下介绍在python的re模块中怎样应用正则表达式

### 1. 使用re.compile
re模块中包含一个重要函数是compile(pattern [, flags]) ，该函数根据包含的正则表达式的字符串创建模式对象。可以实现更有效率的匹配。在直接使用字符串表示的正则表达式进行search,match和findall操作时，python会将字符串转换为正则表达式对象。而使用compile完成一次转换之后，在每次使用模式的时候就不用重复转换。当然，使用re.compile()函数进行转换后，re.search(pattern, string)的调用方式就转换为 pattern.search(string)的调用方式。

其中，后一种调用方式中，pattern是用compile创建的模式对象。如下:

`>>> import re`
`>>> some_text = 'a,b,,,,c d'`
`>>> reObj = re.compile('[, ]+')`
`>>> reObj.split(some_text)`
`['a', 'b', 'c', 'd']`

 

### 2.不使用re.compile
在进行search,match等操作前不适用compile函数，会导致重复使用模式时，需要对模式进行重复的转换。降低匹配速度。而此种方法的调用方式，更为直观。如下:

`>>> import re`
`>>> some_text = 'a,b,,,,c d'`
`>>> re.split('[, ]+',some_text)`
`['a', 'b', 'c', 'd']`
