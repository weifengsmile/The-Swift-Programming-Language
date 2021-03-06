### 基本运算符

运算符就是一个特殊的符号或者词语，你可以用它来检查，更改或者组合一些值。例如，加号(+)可以把两个数字相加，就像`let i = 1 + 2`, 逻辑与运算符(&&)可以把两个布尔值结合起来，比如`if enteredDoorCode && passedRetinaScan`.

你在C语言中的知道的运算符Swift都支持，并且提升了一些用来消除编码错误的能力。等号(=)不会返回一个值，这可以防止在想要使用双等号(==)时误用了它。
算术运算符使用时会检测并且禁止值的溢出，这可以避免当使用的数字可能超出类型所允许的值范围（或更大或更小）时出现意料之外的结果。
**当然你可以选择使用Swift中的溢出运算符来实现值的溢出，具体可以参考[溢出运算符]()章节。

Swift也提供了C语言中没有的范围运算符，比如`a..<b`和`a...b`, 这是一个值的范围表达式的简写。

本章节会介绍Swift常用的运算符。[高级运算符]()章节中会介绍Swift中的高级运算符，并且会介绍如何自定义运算符来实现自定义类型的标准操作。

#### 术语

运算符有一元、二元和三元：
+ 一元运算符只操作一个目标（比如-a）。一元前缀运算符会紧贴目标前出现（比如!b）,一元后缀运算符会紧贴目标后出现（比如c!）.
+ 二元运算符操作两个目标（比如2 + 3）并且是中缀的因为它需要在两个目标中间。
+ 三元运算符操作三个目标，和C语言一样，Swift只有一种三元运算符，三元条件运算符（a ? b : c）.

运算符影响到的值叫做操作数。在表达式`1 + 2`中，加号是一个二元运算符并且两个操作数是值1和2.

#### 赋值运算符

这个赋值运算符（a = b）的作用是初始化或者更新a的值为b的值：
```
let b = 10
var a = 5
a = b
// a is now equal to 10
```

如果等号右边是一个混合值组成的元组，那么它的元素可以被一次性分配给多个常量或变量：
```
let (x, y) = (1, 2)
// x is equal to 1, and y is equal to 2
```

与C语言和Objective-C中的赋值运算符不同的是，Swift中它不会返回一个值。下面的语句是无效的：
```
if x = y {
    // 这是无效的，因为x = y不会返回一个值。
}”
```

这个特点会防止等号在需要用双等号的情况下被误用。Swift通过让x = y无效，来帮助你避免代码中的这类错误。

#### 算术运算符

Swift对所有数字类型都支持四种标准算术运算符：
+ 加（+）
+ 减（-）
+ 乘（*）
+ 除（/）

```
1 + 2       // 等于 3
5 - 3       // 等于 2
2 * 3       // 等于 6
10.0 / 2.5  // 等于 4.0
```

与C和Objective-C中的算术运算符不同，swift默认不允许值的溢出。你可以选择使用Swift中的溢出运算符来实现值的溢出，具体可以参考[溢出运算符]()章节。

加号也支持字符的拼接：
```
hello, " + "world"  // 等于 "hello, world
```

##### 取余运算符

取余运算符（a % b）会计算出a中b的倍数，并返回剩余的值（称为余数）。
```
注意
取余运算符在其他语言中也被叫做取模运算符。但是，在Swift中对负数的该操作严格意义上说，叫做余数而不是模运算。
```

下面是取余操作的过程。要计算`9 % 4`, 第一步需要计算出9中有多少个4:(图)

可以看出，9中有两个4，并且余数是1。
在Swift中，这可以写成：
```
9 % 4  // 等于1
```

要想计算出a % b的答案，%运算符实际上是计算的下面的等式，并把余数作为输出返回:
```
a = (b x some multiplier) + remainder
```

这里的some multiplier是指a中包含的b的最大的倍数。
在等式中插入9和4：
```
9 = (4 x 2) + 1
```

用同样的方法也可以计算负数a的余数：
```
-9 % 4   // 等于 -1
```

在等式中插入-9和4：
```
-9 = (4 x -2) - 1
```

余数是-1.
对于负数b而言，b的负数符号会被忽略，这意味着`a % b`和`a % -b`的结果是一样的。


##### 一元负号

一个数字前加一个一元负号`-`前缀，值就变为相反数。
```
let three = 3
let minusThree = -three       // minusThree 等于 -3
let plusThree = -minusThree   // plusThree 等于 3, 或者-(-3)
```

一元负号是直接紧贴操作数前，中间不能有空格。

###### 一元加号

一元加号会直接返回它所操作的数字值，不会有任何改变：
```
let minusSix = -6
let alsoMinusSix = +minusSix  // alsoMinusSix 等于 -6
```

尽管一元加号实际上什么都没做，但是你可以在正数前面加上它来保持和负数前的负号相对称。

#### 混合赋值运算符

和C语言一样，Swift也提供了混合赋值运算符，它把等号(=)和其它运算符结合在一起。加等于赋值运算符(+=)就是一个例子：
```
var a = 1
a += 2
// a 现在的值是 3
```

表达式`a += 2`就是`a = a + 2`的简写形式。实际上，就是把加号和等号混合在一个运算符中，并且同时发挥两个运算符的作用。
```
注意
混合运算符没有返回值。例如，不能这样写'let b = a += 2'.
```

更多的有关Swift标准库中运算符的信息，可以在[运算符定义]()章节查看。

#### 比较运算符

Swift支持以下比较运算符：
+ 双等于 (a == b)
+ 不等于 (a != b)
+ 大于   (a > b)
+ 小于   (a < b)
+ 大于等于 (a >= b)
+ 小于等于 (a <= b)

```
注意
Swift也提供了两种特殊的运算符(===和!==)，你可以用这个来比较两个对象指针是否指向同一个对象。更多相关信息，请查看[特殊运算符]()章节。
```

每一个比较运算符都会返回一个布尔值，来表示语句结果是否是true：
```
1 == 1   // true 因为 1 等于 1
2 != 1   // true 因为 2 不等于 1
2 > 1    // true 因为 2 大于 1
1 < 2    // true 因为 1 小于 2
1 >= 1   // true 因为 1 大于等于 1
2 <= 1   // false 因为 2 大于 1
```

比较运算符经常用于条件判断语句，比如if语句：
```
let name = "world"
if name == "world" {
    print("hello, world")
} else {
    print("I'm sorry \(name), but I don't recognize you")
}
// Prints "hello, world", because name is indeed equal to "world".
```

更多有关if语句的信息，请查看[控制流]()章节。

你可以比较两个元组，如果他们有相同的类型和相同的元素数量的话。元组的比较是从左到右，一次比较一个值，直到比较到两个值不等即停止。
两两相比，比较的结果决定了元组的比较结果。如果所有元素都两两相等，那么元组就是相等的。例如:
```
(1, "zebra") < (2, "apple")   // true 因为 1 is 小于 2; "zebra" 和 "apple" 无须比较。
(3, "apple") < (3, "bird")    // true 因为 3 等于 3, and "apple" is 小于 "bird"
(4, "dog") == (4, "dog")      // true 因为 4 等于 4, and "dog" 等于 "dog"
```

在上面这个例子中，第一行中你可以看出比较是从左到右的。无论其他的值大小如何，即使后面的"zebra"大于"apple", 因为1小于2，所以(1, "zebra")小于(2, "apple"),第一个元素的大小已经决定了整个元组的大小。但是，如果第一个元素相等，那么就会比较第二个，也就是第二三行的例子。

只有当元组中的每个元素的值都可以被运算符比较时，元组才能够用这个运算符进行比较。例如，下面例子中，你可以比较两个(String, Int)类型的元组，因为String和Int类型都能分别被<比较。与此相反，两个(String, Bool)类型的元组是无法用<比较的，因为<不能用于布尔值比较。
```
("blue", -1) < ("purple", 1)        // OK, evaluates to true
("blue", false) < ("purple", true)  // Error because < can't compare Boolean values
```

```
注意
Swift标准库中提供的元组比较运算符仅限于元素数最多6个的元组，如果要比较的元组的元素数大于或等于7个，就必须自行实现比较运算符。
```

#### 三元条件运算符

三元条件运算符是一种特殊的由三部分组成运算符，三部分是`question ? answer1 : answer2`。它是由一个条件表达式的真假决定的两个表达式之一的值的简写。
如果`question`结果是true，就计算并返回`answer1`的值，否则就计算并返回`answer2`的值。

三元条件运算符是下面代码的简写：
```
if question {
    answer1
} else {
    answer2
}
```

下面是一个计算列表行高的例子。如果行有头部，那么行高应该比内容高度高50point，如果没有头部，高20point：
```
let contentHeight = 40
let hasHeader = true
let rowHeight = contentHeight + (hasHeader ? 50 : 20)
// rowHeight is equal to 90
```

上面的例子实际就是下面代码的简写：
```
let contentHeight = 40
let hasHeader = true
let rowHeight: Int
if hasHeader {
    rowHeight = contentHeight + 50
} else {
    rowHeight = contentHeight + 20
}
// rowHeight is equal to 90
```

第一个例子中三元条件运算符的使用意味着只用一行代码就能给rowHeight设置好值，这比第二个例子中的代码更加简洁。

三元条件运算符在决定使用两个表达式中的一个时提供了简洁的写法。但是请小心使用它，因为如果过度使用，虽然代码更加简洁，但是会导致很难阅读。
另外，要避免在一个复杂语句中组合使用多个三元条件运算符。


#### 空合运算符

空合运算符是指`??`，用法是`a ?? b`，它的意思是，当a有值时则会对a解包并返回值，当a是nil时，返回b的值。
这里的a一定得是一个可选类型变量，同时b必须和a的值类型相同。

空合运算符是下面代码的简写：
```
a != nil ? a! : b
```

上面的代码使用了三元条件运算符，当a不是nil时对a强制解包并返回，否则返回b的值。空合运算符提供了一种简单的方法来对可选类型进行条件检查，并用一种简洁易读的形式对其解包。
```
注意
如果a的值不是nil，那么b的值就不会计算。这也叫做短路计算。
```

下面的例子使用空合运算符来在默认颜色a和可选类型自定义颜色名称之间进行选择：
```
let defaultColorName = "red"
var userDefinedColorName: String?   // defaults to nil

var colorNameToUse = userDefinedColorName ?? defaultColorName
// userDefinedColorName is nil, so colorNameToUse is set to the default of "red"
```

`userDefinedColorName`变量被定义为可选类型字符串，默认值是nil。因为它是可选类型，所以可以使用空合运算符来处理它的值。
在上面的例子中，运算符被用来给字符串变量`colorNameToUse`进行值初始化。因为`userDefinedColorName`是nil，`userDefinedColorName ?? defaultColorName`表达式返回的就是`defaultColorName`的值，也就是'red'。

如果你给`userDefinedColorName`赋一个非nil的值，然后再次使用空合运算符进行检查，就会返回`userDefinedColorName`解包后的值，而不是默认值`defaultColorName`:
```
userDefinedColorName = "green"
colorNameToUse = userDefinedColorName ?? defaultColorName
// userDefinedColorName is not nil, so colorNameToUse is set to "green"
```

#### 区间运算符

Swift提供了几种区间运算符，用来表示一个值区间。

##### 闭区间运算符

闭区间运算符`a...b`定义了一个从a到b的区间，并且包含a和b。a的值一定不大于b。
闭区间运算符用于对一个包含区间内所有值的区间的遍历，比如用于for-in循环：
```
for index in 1...5 {
    print("\(index) times 5 is \(index * 5)")
}
// 1 times 5 is 5
// 2 times 5 is 10
// 3 times 5 is 15
// 4 times 5 is 20
// 5 times 5 is 25
```

有关for-in循环的更多介绍，请查看[控制流]()章节


##### 半开区间运算符

半开区间运算符`a..<b`定了一个从a到b的区间，但是不包含b。之所以叫半开区间，是因为它包含了区间第一个值，但不包含最后一个值。
和闭区间一样，它的a值也一定不能大于b。如果a和b的值一样，那么这个区间就是空的。半开区间对于以零为开头的列表比如数组很有用，他可以很方便地算出列表的长度：
```
let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count
for i in 0..<count {
    print("Person \(i + 1) is called \(names[i])")
}
// Person 1 is called Anna
// Person 2 is called Alex
// Person 3 is called Brian
// Person 4 is called Jack
```

注意，数组包含4个元素，但是`0..<count`只能数到3（即数组最后一个元素的下标），因为这是一个半开区间。更多数组相关的介绍，请查看[数组]()章节。

##### 单边区间

有另外一种类似于闭区间的区间形式，它在一个方向上没有边界。例如，一个包含从下标2开始到数组结束的区间。这里你可以忽略区间一边的值，这种区间就叫做单边区间，因为它只有一边有值。例如：
```
for name in names[2...] {
    print(name)
}
// Brian
// Jack

for name in names[...2] {
    print(name)
}
// Anna
// Alex
// Brian
```

半开区间运算符也有一种单边的形式，他只有结束的那边的值。同样的，最大的这个值也不在区间之内。例如：
```
for name in names[..<2] {
    print(name)
}
// Anna
// Alex
```

单边区间除了在下标方面有应用，在其他的场景也有应用。你不能遍历一个没有初始值的单边区间，因为这并没有一个清楚的起始值。但是你可以遍历一个忽略结束值的单边区间。
然而，由于这种区间可以无限延伸下去，所以你必须给他一个明确的遍历结束的条件。你可以像下面的代码一样，检查一个单边区间是否包含一个特殊的值。
```
let range = ...5
range.contains(7)   // false
range.contains(4)   // true
range.contains(-1)  // true
```

#### 逻辑运算符

逻辑运算符的作用是修改或者合并`true`和`false`这样的逻辑布尔值。Swift支持C系语言中的三种标准逻辑运算符：
+ 逻辑否(!a)
+ 逻辑与(a && b)
+ 逻辑或(a || b)

##### 逻辑否运算符

逻辑否运算符(!a)的作用是把一个布尔值取否，比如把true变为false，false变为true。
逻辑否运算符是一个前缀运算符，并且要紧贴被操作变量，中间不能有空格。意思是'not a'，下面是一个例子：
```
let allowedEntry = false
if !allowedEntry {
    print("ACCESS DENIED")
}
// Prints "ACCESS DENIED"
```

语句`if !allowedEntry`的意思是‘如果不被允许进入’。从句只能在‘不被允许进入’为`true`时才会执行，也就是`if allowedEntry`为false时。

就像上面这个例子一样，对布尔变量或常量名字的慎重选择有助于保持代码的良好可读性和简洁性，尽量避免出现双重否定或者混乱逻辑的语句。

##### 逻辑与运算符

逻辑与运算符的作用是创建一个逻辑表达式，这个表达式只有所有值都是true时，整个表达式的值才是true。
如果其中一个值是false，整个表达式的值就是false，实际上，如果第一个值就是false的话，第二个值甚至不会去计算，因为它无法改变整个值是false的事实。
这也叫做短路计算。

下面这个例子就是只有两个值都是true时才会打印"Welcome!"：
```
let enteredDoorCode = true
let passedRetinaScan = false
if enteredDoorCode && passedRetinaScan {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Prints "ACCESS DENIED"
```

##### 逻辑或运算符

逻辑或运算符是一种由两个管道符组成的中缀运算符。你可以用它来创建一个逻辑表达式，在这个表达式中只要有一个值是true，那么整个表达式的值就是true。
和上面的逻辑与表达式一样，逻辑或运算符也采用了短路计算的方法。如果表达式左边的值是true，那么右边的值就不会计算，以为右边的值已经无法改变整个表达式的值了。

在下面的例子中，第一个布尔值(hasDoorKey)是false，但是第二个值(knowsOverridePassword)是true,因为有一个值是true，所以整个表达式的值就是true，即允许通过：
```
let hasDoorKey = false
let knowsOverridePassword = true
if hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Prints "Welcome!"
```

##### 混合逻辑运算符

你可以把多个逻辑运算符组合到一起变成一个更长的混合表达式：
```
if enteredDoorCode && passedRetinaScan || hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Prints "Welcome!"
```

这个例子中用到了多个`&&`和`||`运算符来创建了一个更长的混合表达式。但是，每个`&&`和`||`仍然只操作两个值，因此，实际上这是把三个短的表达式串联在一起。它的意思是：
如果我们已经进入了正确的门号并且通过了视网膜扫描，或者有门的钥匙，或者知道紧急密码，那么就允许通过。

基于三个变量的值，如果前两个的值是false但是知道紧急密码，那么整个表达式的值仍然是true。
```
注意
Swift的逻辑运算符&&和||都是从左向右计算的，也就是说多个逻辑运算符组成的混合表达式都是从最左边开始计算子表达式的。
```

#### 明确的圆括号

在不必使用括号的情况下使用括号有时也是有用的，它可以让复杂的表达式变得更加清晰，增强其可读性。在上面的进门的例子中，在混合表达式的第一个部分加上圆括号是很有用的，可以更清楚地指明语句的意图：
```
if (enteredDoorCode && passedRetinaScan) || hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Prints "Welcome!"
```

圆括号可以让前两个值在整个逻辑中清晰地结合成一部分来计算。并且整个混合表达式的结果也没有发生变化，只是整个逻辑意图更加容易理解。
易读性总是优先于简洁性的，使用圆括号有助于让你的意图更加清晰。

