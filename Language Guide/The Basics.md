#### 常量和变量

常量和变量关联了一个名称（比如`maximumNumberOfLoginAttempts`或者`welcomeMessage`）和一个特定类型的值（比如数字10或者字符串"Hello"）。常量的值一旦设定好就不允许改变，但变量可以改变。

##### 声明常量和变量

常量和变量在使用前必须先声明。你可以用使用`let`关键字来声明常量，用`var`关键字来声明变量。这里有一个例子，展示了追踪一个用户尝试登陆次数场景中，常量和变量是如何使用的：
```
let maximumNumberOfLoginAttempts = 10
var currentLoginAttempt = 0
```

这段代码的意思是：
声明一个名为`maximumNumberOfLoginAttempts`的常量,给它赋值为10，然后，声明一个名为`currentLoginAttempt`的变量，并且给它一个初始值为0。
在这个例子中，允许尝试登陆的最大次数声明为常量，因为最大值不能改变。当前尝试登陆次数被声明为变量，因为这个值在每次登录尝试失败后再次尝试时一定会增加。

你可以在单行代码中声明多个常量或多个变量，中间用逗号分开即可：
```
var x = 0.0, y = 0.0, z = 0.0
```

```
注意
如果你代码中的一个值永远不变，那么就用let关键字把它声明为一个常量。只有当它需要改变时才使用变量。
```

##### 类型注释

当声明一个常量或者变量时，可以使用类型注释来指明此常量或者变量所存储的值的类型。在常量或者变量名称后加上冒号空格和类型即可完成类型注释。
下面这个例子给一个名叫`welcomeMessage`的变量提供了一个类型注释，表明了它可以存储字符串类型的值：
```
var welcomeMessage: String
```

冒号的意思是：……的类型，所以上面的代码意思是：“声明了一个名叫`welcomeMessage`的字符串类型变量。”
现在这个变量可以被赋予任何字符串值而不报错。
```
welcomeMessage = "Hello"
```

你可以在单行代码中定义多个相同类型的变量，中间用逗号分开，最后一个变量后面加上类型注释即可。
```
var red, green, blue: Double
```

```
注意
在实际使用中，很少有需要类型注释的情况。如果在常量或者变量被定义时就赋予它一个初始值，Swift可以根据这个值推断出它们的类型，这叫做“类型安全和类型推断”。在上面welcomeMessage的例子中，没有提供一个初始值，所以它的类型直接用类型注释指明，而不是由初始值推断出来。
```

##### 常量和变量命名

变量和常量的名称可以包含几乎任何字符，包括Unicode字符：
```
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "dogcow"
```

变量和常量的名称不能包含空格，数学符号，箭头，私有Unicode标量，横线和制表符。同时既不能以数字开头，也不能在其中包含任何数字。
一旦已经声明了一个确定类型的变量或常量，就不能再用同样的名称再次声明，也不能改变它存储的值类型。同时，常量不能变成变量，变量也不能变成常量。
```
注意
如果你需要用Swift保留关键字作为变量或常量的名称，那么需要在关键字周围用"`"包裹即可。但是，除非你的确没有其他选择了，否则应该避免使用保留关键字作为变量名称。
```

你可以改变一个已定义的变量值，在这个例子中，`friendlyWelcome`变量值由"Hello"变为"Bonjour"。
```
var friendlyWelcome = "Hello!"
friendlyWelcome = "Bonjour!"
// friendlyWelcome is now "Bonjour!"
```

与变量不同，常量一旦赋值就不能改变。试图改变常量的值会在代码编译时报错：
```
let languageName = "Swift"
languageName = "Swift++"
// This is a compile-time error: languageName cannot be changed.
```

##### 打印常量和变量

你可以使用`print(_:separator:terminator:)`函数来打印常量或者变量的当前值：
```
print(friendlyWelcome)
// Prints "Bonjour!"
```

这里的`print(_:separator:terminator:)`函数是一个打印一个或多个值到适当的输出处的全局函数。例如在Xcode中，这个函数会把输出结果打印到xCode的控制台中。separator和terminator参数有默认值，所以你可以在调用时忽略它。默认情况下，这个函数会在打印的行尾增加一个换行符。如果要打印出尾部没有换行符，那么需要传一个空字符串作为terminator参数值。例如，`print(someValue, terminator: "")`。如果要获取更多有关参数默认值的信息，请查看[默认参数值]()。

Swift使用字符串插值将常量或变量的名称作为占位符包含在较长的字符串中，并提示Swift将其替换为该常量或变量的当前值。将名称括在括号中，并在左括号前用反斜杠转义：
```
print("The current value of friendlyWelcome is \(friendlyWelcome)")
// Prints "The current value of friendlyWelcome is Bonjour!"
```

```
注意
你可以使用的字符串插值选项可以在[字符串插值]()中查看。
```

#### 注释

代码中的非执行文本会被注释掉作为笔记或者提醒。注释会被Swift编译器在编译时忽略。
Swift中的注释和C语言中的很类似，使用双斜杠开头来注释单行文本。
```
// This is a comment.
```

使用单斜杠和星号开头以及星号和单斜杠结尾来注释多行文本。
```
/* This is also a comment
but is written over multiple lines. */
```

与C语言中的多行注释不同，Swift中的多行注释允许在其他多行注释中嵌套。编写嵌套注释的方法是先写一个多行注释块，然后在第一个块中嵌入第二个多行注释。然后先关闭第二个块，然后关闭第一个块：
```
/* This is the start of the first multiline comment.
 /* This is the second, nested multiline comment. */
This is the end of the first multiline comment. */
```

嵌套注释使得你可以快速简单地注释掉大段代码，即使代码中已经包含有多行注释。

##### 分号

与其他语言不同，Swift不要求在每行代码最后加写分号，当然你愿意的话也可以加上。但是，当你在一行代码中写多个语句时，分号必须加上。
```
let cat = "🐱"; print(cat)
// Prints "🐱"
```

##### 整数

整数是没有分数部分的数字，例如42和-23。整数分为有符号数(正数，零和负数)和无符号数(正数和零)。

Swift提供了8、16、32和64位的有符号和无符号整数。这些正数沿用了类似于C语言的命名习惯：8位无符号数为UInt8类型，32位有符号数为Int32类型。与Swift中的所有类型一样，这些整数类型的名称都是大写开头的。

###### 整数范围

你可以用整数的`min`和`max`属性来获取每种整数类型所能表示的最小和最大值：
```
let minValue = UInt8.min  // minValue is equal to 0, and is of type UInt8
let maxValue = UInt8.max  // maxValue is equal to 255, and is of type UInt8
```

这些属性的值具有适当大小的数字类型（如上例中的UInt8），因此可以在表达式中与相同类型的其他值一起使用。

###### Int

在大部分情况下，你不需要在代码中指明你要使用的整数大小。Swift提供了额外的一个整数类型，`Int`， 这个类型会拥有跟平台位数一样的大小：
```
在32位平台上，Int和Int32占用同样空间大小。
在64位平台上，Int和Int64占用同样空间大小。
```

除非你的确需要指明整形的大小，否则在你的代码始终使用`Int`代表整数即可。这有助于代码的统一和互操作。
即使在32位平台上，Int类型也可以存储任意一个在-2,147,483,648和2,147,483,647之间的整数，
这对很多整数范围而言已经足够大了。

###### UInt

Swift也提供了一种无符号整数类型`UInt`, 这个类型会拥有跟平台位数一样的大小：
```
在32位平台上，UInt和UInt32占用同样空间大小。
在64位平台上，IUnt和UInt64占用同样空间大小。
```

```
注意
只有当你明确需要一个和当前平台位数相同的无符号整数类型时，才使用UInt。
否则，即使知道存储的值是非负数,使用Int类型也更合适。对整数类型统一使用Int有助于代码的互操作性，
这可以避免在不同数字类型之间的相互转换，与整数的类型推断也相匹配，这里可以在[类型安全和类型推断]()中有描述。
```

##### 浮点数

浮点数是有小数部分的数字，比如3.14159，0.1以及-273.15.
浮点数类型可以代表比整数范围更大的数字，并且可以存储比Int数字大得多或者小得多的数字。Swift提供了两种浮点数类型：
+ `Double`代表64位精度浮点数。
+ `Float`代表32位精度浮点数。

```
注意
Double类型拥有至少15位小数的精度，而Float是6位。实际使用当中，究竟哪种浮点数类型更合适取决于你的代码中数字值的性质和范围。
如果两种都可以，那么优先使用Double更好些。
```

#### 类型安全和类型推断

Swift是一种类型安全的语言。一种类型安全的语言会鼓励你明确代码中的值的类型。如果你的代码需要String类型，那么就不能错误地传递给他Int类型。
由于它的类型安全，Swift会在代码编译时进行类型检测，并且把类型的误使用标记成错误。这就可以让你在开发过程中尽可能早地发现并修正错误。

类型检查会在你使用不同类型变量时帮助你避免错误使用，但是，这不意味着你必须要每次都显式声明每个常量或者变量的类型。如果你没有给你所使用的值标明类型，Swift会使用类型推断推断出合适的类型。类型推断会使编译器在编译代码时，简单地根据你所提供的初始值来自动推断出特定表达式的值类型。

正是由于有了类型推断，相比于像C或者Objective-C之类的语言，Swift几乎很少要求对变量进行类型声明。常量和变量仍然是类型明确的，只不过大部分类型确定的工作都已经自动为你做好了。

类型推断尤其是在你声明了一个有初始值的常量或者变量时有用处。这个过程其实就是在声明常量或者变量时，给它一个字面量。（一个字面量就是源代码中直接出现的那个值，比如下面例子中的42和3.14159）。

例如，如果你新建了一个常量，但是没有指明它的类型，却给了它一个字面量42，Swift就会推断出你想要这个常量的类型是Int，因为你用了一个像整数一样的数字来初始化它：
```
let meaningOfLife = 42
// meaningOfLife is inferred to be of type Int
```

同样的，如果你没有给浮点数的字面量指明类型，Swift也会推断出你想创建一个Double类型：
```
let pi = 3.14159
// pi is inferred to be of type Double
```

对于浮点数的类型推断，Swift总是会选择Double而不是Float类型。
如果你在一个表达式里组合了整数和浮点数，那么根据上下文推断出来的还是Double类型：
```
let anotherPi = 3 + 0.14159
// anotherPi is also inferred to be of type Double
```

上面例子中，3的字面量类型没有明确，所以由于表达式中另一部分浮点数的出现，推断出输出Double类型是比较合适的。

##### 数值的字面量

整数的字面量可以写成：
+ 无前缀的十进制数字。
+ 以`0b`为前缀的二进制数字。
+ 以`0o`为前缀的八进制数字。
+ 以`0x`为前缀的十六进制数字。

下面所有的整数字面量的十进制值都是17：
```
let decimalInteger = 17
let binaryInteger = 0b10001       // 17 in binary notation
let octalInteger = 0o21           // 17 in octal notation
let hexadecimalInteger = 0x11     // 17 in hexadecimal notation
```

浮点数的字面量可以是无前缀的十进制数，或者以`0x`为前缀的十六进制数。它们的小数点两边都必须有一个数字（或十六进制数）。十进制的浮点数可以有一个可选择的由大写或者小写e表示的指数。十六进制的浮点数必须要有一个由大写或者小写p表示的指数。
对于指数为exp的十进制数，值就是基数乘以10<sup>exp</sup>。

+ 1.25e2 等于 1.25 x 102, 或者 125.0.
+ 1.25e-2 等于 1.25 x 10-2, 或者 0.0125.

对于指数为exp的十六进制数，值就是基数乘以2<sup>exp</sup>。

+ 0xFp2 等于 15 x 22, 或者 60.0.
+ 0xFp-2 等于 15 x 2-2, 或者 3.75.

下面这些所有浮点数的字面量的十进制都是12.1875：
```
let decimalDouble = 12.1875
let exponentDouble = 1.21875e1
let hexadecimalDouble = 0xC.3p0
```

数字的字面量允许包含其他额外的格式来使其具有更好的可读性。无论是整数还是浮点数，都可以用额外的零进行填充，并且可以添加下划线来增强可读性。下面的字面量都不会因为格式化而改变：
```
let paddedDouble = 000123.456
let oneMillion = 1_000_000
let justOverOneMillion = 1_000_000.000_000_1
```

##### 数字类型转换

对于所有通用的整数型常量或变量，即使明确它们是非负数，也要使用Int类型。在每个场景中都使用这个默认的整数类型就意味着你代码中的整数型常量和变量是可以直接互相操作的，并且这也和整数型字面量所推断出的类型相一致。

只有当手边的任务有明确的需要，比如来自外部资源数据的大小明确，出于性能考虑的内存使用或其他必要优化时，才会使用其他整数类型。
在这些情况下使用明确大小的类型有助于捕获任何意外的值溢出，并隐式记录所使用数据的性质。

###### 整型转换

整型常量或者变量所存储的值的范围是随着不同的数字类型而不同的。Int8类型的常量或变量所能存储的数字范围是-128到127，与此相对的UInt8的范围是0到255。
当数字不在整型大小范围内时，编译器就会报错：
```
let cannotBeNegative: UInt8 = -1
// UInt8 cannot store negative numbers, and so this will report an error
let tooBig: Int8 = Int8.max + 1
// Int8 cannot store a number larger than its maximum value,
// and so this will also report an error
```

由于不同的数字类型所存储的值范围不同，你必须根据实际情况进行类型转换。这个方法可防止隐藏的转换错误，并有助于在代码中明确表示类型转换意图。
为了把一个指定数字类型转换为另外一个，你可以用已出现的值初始化一个目标类型的新数字。在下面的例子中，常量`twoThousand`是UInt16类型的，`one`是UInt8类型的。他们不能直接相加，因为他们不是同一个类型。相反，这个例子调用了`UInt16(one)`方法用原来的值初始化出一个UInt16类型的值，并以此来替代原有的值进行相加操作。
```
let twoThousand: UInt16 = 2_000
let one: UInt8 = 1
let twoThousandAndOne = twoThousand + UInt16(one)
```

由于加号两边的值类型都是UInt16，相加操作才被允许。输出的结果`twoThousandAndOne`类型被推断为UInt16, 因为它是两个UInt16值的和。

SomeType（ofInitialValue）这种方法是以传递初始值作为参数来调用Swift的类型构造器的默认方法。在这个场景背后，UInt16有一个构造器方法，它允许接收一个UInt8的值，所以这个构造器就可以被用来从已出现的UInt8类型创建一个新的UInt16类型。但是这里你不能传递任何其他类型，这个类型必须是UInt16提供的构造器所接收的才行。扩展已出现的类型来使其提供接收新类型（包括自定义的类型）的构造器会在[扩展]()章节中介绍。

###### 整形和浮点型转换

整型和浮点型数字类型的转换必须显示标明：
```
let three = 3
let pointOneFourOneFiveNine = 0.14159
let pi = Double(three) + pointOneFourOneFiveNine
// pi equals 3.14159, and is inferred to be of type Double
```
这里，常量`three`的值被用来创建一个同样值的Double类型，以此来保证加号两边具有同样的类型。没有这里的转换，加法是不被允许的。

浮点数转成整数也一定要显示标明。一个整数类型可以用一个Double或者Float类型的值来初始化：
```
let integerPi = Int(pi)
// integerPi equals 3, and is inferred to be of type Int
```

浮点数用这种方法转换成整型总是会被舍去小数部分而变小，这就意味着，4.75变成4， -3.9变成-3。
```
注意
数字常量和变量的组合规则是随着数字字面量不同而不同的。字面量3可以直接和字面量0.14159相加，是因为数字字面量没有显式的类型。
只有在编译器对其求值时才推断出它们的类型。
```


#### 类型别名

类型别名定义了一个已出现类型的另外一个名字。你可以用`typealias`关键字来定义类型别名。
当你希望用一个上下文更合适的名字来代指一个类型时，类型别名是很有用的。例如在处理来自外部源的特定大小的数据时：
```
typealias AudioSample = UInt16
```

一旦定义好了类型别名，就可以在任何用到原来名字的地方使用这个别名：
```
var maxAmplitudeFound = AudioSample.min
// maxAmplitudeFound is now 0
```

这里，`AudioSample`就被定义成了UInt16类型的别名。因为它是一个别名，所以调用`AudioSample.min`实际上就是调用的`UInt16.min`，这个值是0，被提供给变量`maxAmplitudeFound`作为其初始值。


#### 布尔值

Swift有一种基础的`Boolean`类型，叫做`Bool`。布尔值被称为逻辑值，因为他们只能是真或者假。Swift给布尔类型提供了两个常量，`true`和`false`:
```
let orangesAreOrange = true
let turnipsAreDelicious = false
```

`orangesAreOrange`和`turnipsAreDelicious`两个变量由于初始值是布尔型字面量，所以会被自动推断为Bool类型。就像前面我们提到的Double和Int类型一样，在创建变量或常量时，不必声明类型为Bool，给他们赋予true或者false的初始值即可。在用已知类型的值来初始化变量或者常量时，类型推断会帮助Swift代码变得简洁和易读。

布尔值在在使用像if语句一样的条件语句时会特别有用：
```
if turnipsAreDelicious {
    print("Mmm, tasty turnips!")
} else {
    print("Eww, turnips are horrible.")
}
// Prints "Eww, turnips are horrible.
```

像if语言一样的条件语句会在[控制流]()章节有更详细的介绍。

Swift的类型安全会防止非布尔值替代布尔值，下面这个例子就会抛出编译错误：
```
let i = 1
if i {
    // this example will not compile, and will report an error
}
```

但是，下面这个例子是有效的:
```
let i = 1
if i == 1 {
    // this example will compile successfully
}
```

`i == 1`比较的结果就是Bool类型，因此第二个例子会通过类型检查。像`i == 1`这种比较表达式在[基本操作符]()章节有介绍。

和Swift中其他的类型安全的例子一样，这种方法会避免意外错误的发生，并且可以确保一段特定的代码的意图清晰明确。

元组会把多个值组合到一起成为一个单一的混合值。一个元组中的值可以是任何类型，并且各个值不必是同一种类型。
在这个例子中，`(404, "Not Found")`就是一个面熟HTTP状态码的元组。一个HTTP状态码是当你请求网页数据时，由web服务端返回的特殊值。当你请求的网页不存在时，返回的状态码就是“404 Not Found”。
```
let http404Error = (404, "Not Found")
// http404Error is of type (Int, String), and equals (404, "Not Found")
```

这个`(404, "Not Found")`元组是把一个Int类型和一个String类型的值组合在一起，这两部分就是HTTP状态码的数字部分和人类可读的描述部分。
他可以被描述为“一个类型为`(Int, String)`”的元组。

你可以用任何排列组合的方式来创建一个元组，并且其中包含的任意不同的类型。比如这样`(Int, Int, Int)`或者这样`(String, Bool)`或者其他你需要的任何排列组合。

你可以从一个元组中解析出单个的变量或者常量，通常的做法如下：
```
let (statusCode, statusMessage) = http404Error
print("The status code is \(statusCode)")
// Prints "The status code is 404"
print("The status message is \(statusMessage)")
// Prints "The status message is Not Found
```

当你分解析元组时，如果你只需要元组中的一部分值，那么其余不需要的值可以使用下划线(_)来忽略其他部分值：
```
let (justTheStatusCode, _) = http404Error
print("The status code is \(justTheStatusCode)")
// Prints "The status code is 404
```

还有一点，你可以使用从零开始的数字下标来访问元组中单一元素的值：
```
print("The status code is \(http404Error.0)")
// Prints "The status code is 404"
print("The status message is \(http404Error.1)")
// Prints "The status message is Not Found"
```

你还可以在元组定义时，给其中的每个元素命名：
```
let http200Status = (statusCode: 200, description: "OK")
```

如果你给每个元素都命名了，那么就可以用这些名字来访问这些元素的值：
```
print("The status code is \(http200Status.statusCode)")
// Prints "The status code is 200"
print("The status message is \(http200Status.description)")
// Prints "The status message is OK"
```

元组在作为函数返回值时尤其有用。比如一个试图获取网页的函数可以返回一个`(Int, String)`类型的元组，来描述请求的成功或者失败。
相比于只返回一个单一类型的值，通过返回一个拥有两个不同类型不同值的元组，函数可以提供更多有关它的结果的有用信息。要获取更多相关信息，
可以参考[多返回值的函数]()章节。

```
注意
元组对把相关联的值简单组合在一起很有用。但它们不适用于创建复杂的数据结构。如果你的数据结构很可能更复杂，
那么把它定义成类或者结构体更合适。要获取更多相关信息，可以参考"结构体和类"章节。
```

#### 可选类型

当一个值可能不存在时你就可以使用可选类型了。可选类型代表了两种可能：要么有一个值，并且你可以对整个变量解包来访问这个值，要么值根本不存在。
```
注意
可选类型的概念在C或者Objective-C中是不存在的。Objective-C中最接近可选类型的就是本该返回一个对象的函数返回了nil，代表“无有效对象”。
然而，这也仅仅只局限于类，对结构体，C语言基本类型以及枚举类型是不存在返回nil这种情况的。
对这些类型来说，Objective-C的方法一律会返回一个特殊的值（比如NSNotFound）来代表值的不存在。
这个方法会假定函数的调用者知道有一个特殊值要测试，并记得要检查它。
Swift的可选类型允许你让任何类型的值都不存在，而不需要特殊的常量。
```

这里是一个可选类型如何被用来处理值不存在的例子。Swift的Int类型有一个构造器方法可以把String类型转换为Int类型。
然而，不是所有的字符串都能够转换成整数。字符串”123“可以被转换成数字123，但是字符串”Hello, World“不能。
下面这个例子就是用构造器方法试图把String类型转为Int类型：
```
let possibleNumber = "123"
let convertedNumber = Int(possibleNumber)
// convertedNumber is inferred to be of type "Int?", or "optional Int
```

由于构造器方法也许会失败，所以它的返回结果是可选的Int类型，而不是Int类型。可选的Int类型写作`Int?`, 不是`Int`。
这个问号代表了它的值是可选的，意味着它肯能包含一些Int类型的值，也可能根本不包含任何值。
（但它不能包含任何其他的类型值，比如布尔值或者字符串值，它要么是一个Int值，要么什么值都没有。）

##### nil
你可以通过赋一个特殊的值nil来把一个可选类型变量设为无值状态。
```
var serverResponseCode: Int? = 404
// serverResponseCode contains an actual Int value of 404
serverResponseCode = nil
// serverResponseCode now contains no value
```

```
注意
你不能把nil赋给一个非可选类型的变量或者常量。如果一个常量或者变量在当前条件下需要有一个无值状态，那么把它生命成合适类型的可选值即可。
```

如果你定义了一个可选类型变量，但是没有给他默认值，那么这个变量会自动被赋予nil值：
```
var surveyAnswer: String?
// surveyAnswer is automatically set to nil
```

```
注意
Swift的nil和Objective-C中的nil是不一样的。Objective-C中的nil是一个指向不存在的对象的指针。而Swift中，nil不是一个指针，它代表一个
类型值的缺失。任何类型的可选值都可以设为nil，不仅仅是对象类型。
```

#### If语句和强制解包

你可以使用if语句来通过把可选类型变量和nil相比来判断它是否有值。这个比较可以用”==“或者”!=“来完成.
如果可选类型有值，那么它一定不等于nil：
```
if convertedNumber != nil {
    print("convertedNumber contains some integer value.")
}
// Prints "convertedNumber contains some integer value.
```

一旦你确定可选类型有值，那么你可以在变量名后面加感叹号(!)来访问它的值。这个感叹号的作用是说，”我知道这个可选类型变量的确有值，请直接使用吧。“
这个就是可选类型的强制解包：
```
if convertedNumber != nil {
    print("convertedNumber has an integer value of \(convertedNumber!).")
}
// Prints "convertedNumber has an integer value of 123.
```

想要了解更多有关if语句的信息，请参考[控制流]()章节。

```
注意
如果使用!来访问一个没有值的可选类型变量会触发一个运行时错误。所以在使用!进行强制解包前一定要确保可选类型包含一个非nil的值。
```

#### 可选绑定

你可以使用可选绑定来判断一个可选类型是否有值，并且如果有值的话，这个值可以被直接赋予一个临时的常量或者变量。
可选绑定通常会被用在if和while的条件语句中来检查可选类型的值，并且会把值赋给一个常量或变量作为操作的一部分。if和while语句在[控制流]()章节中有更详细的介绍。

在if语句中写一个可选绑定，如下：
```
if let constantName = someOptional {
    statements
}
```

你可以重写可选类型章节中`possibleNumber`这个例子，来使用可选绑定而不是强制解包：
```
if let actualNumber = Int(possibleNumber) {
    print("The string \"\(possibleNumber)\" has an integer value of \(actualNumber)")
} else {
    print("The string \"\(possibleNumber)\" could not be converted to an integer")
}
// Prints "The string "123" has an integer value of 123
```

这段代码的意思是：
"如果`Int(possibleNumber)`返回的可选Int类型包含值，那么就把这个值赋给一个叫做`actualNumber`的常量"
如果转换是成功的，`actualNumber`常量就可以在if语句的代码块中被访问和使用，并且这个常量也用这个可选类型所包含的值初始化过了，
所以访问`actualNumber`时就不需要在后缀使用!进行解包操作。在这个例子中，`actualNumber`被简单地用来打印转换结果。

变量和常量都支持使用可选绑定。如果你想要在if语句的第一段代码块中更改`actualNumber`的值，那么你可以写成`if var actualNumber`,
这个可选类型中包含的值将会作为变量而不是常量被访问。

你可以根据需要在一个if语句中包含多个可选绑定和布尔值条件，它们之间用逗号分开即可。
如果其中任何一个可选绑定的值是nil或者任何一个布尔条件的值是false，那么整个if语句的条件就是false。
下面的if语句是等效的：
```
if let firstNumber = Int("4"), let secondNumber = Int("42"), firstNumber < secondNumber && secondNumber < 100 {
    print("\(firstNumber) < \(secondNumber) < 100")
}
// Prints "4 < 42 < 100"

if let firstNumber = Int("4") {
    if let secondNumber = Int("42") {
        if firstNumber < secondNumber && secondNumber < 100 {
            print("\(firstNumber) < \(secondNumber) < 100")
        }
    }
}
// Prints "4 < 42 < 100"
```

```
注意
在if语句中由可选绑定所创建的常量和变量仅在if语句的代码块中是可用的。
与此相反，在一个guard语句中创建的常量和变量在guard下方的代码中都是可用的。这在[提前退出]()章节中有介绍。
```

#### 可选类型的隐式解包

正如上面所描述的，可选类型表明一个常量或变量允许不存在值。可选类型可以在if语句中判断出其值是否存在，
并且如果存在值的话，可以使用可选绑定的方法来对其解包进而访问它的值。

有时从程序的结构中可以清楚地看出一个可选类型在初次赋值后总是有值。在一些场景中，由于可选类型可以很安全地被假定总是有值，所以每次访问它时，移除对它的检查和解包是很有用的。

这种可选类型被定义为隐式解包可选类型。你可以通过在类型后加感叹号而不是问号来定义一个隐式解包的可选类型。
不是像之前那样在使用变量时，在可选类型变量后加感叹号，而是在声明可选类型时在类型后面加感叹号。

当一个可选类型的值在被定义时就存在并且在之后可以确定都一直存在，此时隐式解包就很有用。Swift中隐式解包的主要应用是在类的初始化中，在[Unowned References and Implicitly Unwrapped Optional Properties]()章节中有介绍。

在这些场景背后，隐式解包的可选类型就是一个普通的可选类型，只不过可以像非可选类型一样使用，并且在每次被访问时无须进行解包。
下面的例子展示了一个可选类型字符串和一个隐式解包可选类型字符串在访问它们的值时的不同之处：
```
let possibleString: String? = "An optional string."
let forcedString: String = possibleString! // requires an exclamation point

let assumedString: String! = "An implicitly unwrapped optional string."
let implicitString: String = assumedString // no need for an exclamation point
```

你可以把隐式解包的可选类型想象成在需要时有权限强制解包的可选类型。当你使用一个隐式解包可选类型的值时，Swift首先会把它当做一个普通的可选类型值来使用，
如果它不能被当作可选类型使用时，就会对它强制解包。在上面的代码中，可选类型assumedString的值在赋给implicitString之前进行了强制解包，因为implicitString不是可选类型，就是一个字符串类型。
在下面的代码中，optionalString没有一个明确的类型因为它是一个普通的可选类型。
```
let optionalString = assumedString
// The type of optionalString is "String?" and assumedString isn't force-unwrapped.
```

如果一个隐式解包可选类型的值是nil，此时你试图获取它的值，就会触发一个运行时错误。这个结果和你试图通过感叹号来获取一个不存在值的普通可选类型是一样的。
你可以用检查普通可选类型的值的方式来检查隐式解包可选类型的值是否是nil：
```
if assumedString != nil {
    print(assumedString!)
}
// Prints "An implicitly unwrapped optional string.
```

你也可以在一个语句中对隐式解包的可选类型使用可选绑定来检查并获取它的值：
```
if let definiteString = assumedString {
    print(definiteString)
}
// Prints "An implicitly unwrapped optional string.
```

```
注意
当一个变量在随后的某个地方可能变为nil时，请不要使用隐式解包的可选类型。
在一个变量的生命周期中，如果你需要对它进行nil检查，那么就使用普通可选类型。
```

#### 错误处理

你可以使用错误处理来对程序运行中可能遇到的错误进行响应。与可选类型使用值的存在与不存在来代表函数的成功与否不同，错误处理允许定义错误的类型，并且如果有必要的话，可以把错误抛给程序的另一部分去处理。

当一个函数内部发生了错误，它就会抛出这个异常。这个函数的调用者可以使用`catch`来捕捉这个异常并作出合适的处理。
```
func canThrowAnError() throws {
    // this function may or may not throw an error
}
```

一个函数在声明时包含`throw`关键字就代表它可以抛出错误。当你调用这种可以抛出错误的异常时你需要在语句前加上`try`关键字。

Swift会自动把当前作用域的错误向上抛出直到遇到一个`catch`分句来处理错误。
```
do {
    try canThrowAnError()
    // no error was thrown
} catch {
    // an error was thrown
}
```

用`do`关键字创建一个作用域，在这个作用域中的错误允许被传递到一个或多个`catch`语句中进行处理。

这里是一个用错误处理来处理不同错误条件的例子：
```
func makeASandwich() throws {
    // ...
}

do {
    try makeASandwich()
    eatASandwich()
} catch SandwichError.outOfCleanDishes {
    washDishes()
} catch SandwichError.missingIngredients(let ingredients) {
    buyGroceries(ingredients)
}
```

在这个例子中，如果没有干净的盘子或者任何原材料缺少，那么makeASandwich函数就会抛出一个错误。
因为这个函数可能会抛出错误，所以它的调用者需要用`try`表达式去调用它。通过把函数调用放在一个`do`语句中，任何错误都会传递到`catch`从句中进行处理。

如果没有错误抛出，那么就会继续执行下面的eatASandwich方法。
如果有错误抛出，并且错误类型是SandwichError.outOfCleanDishes，那么就会走第一个case,将会执行washDishes方法。同样的，如果错误类型是SandwichError.missingIngredients，那么就会走第二个case，执行buyGroceries方法，同时相关的字符串值也会被catch所传递进去。

错误的抛出，捕获以及传递都会在[错误处理]()章节有更详细的介绍。

#### 断言和先决条件

断言和先决条件是在运行时进行的检查。你可以使用他们来确保在执行更深处的代码之前一个重要条件必须满足。如果断言或者先决条件中的布尔条件结果是true，那么代码会继续照常执行。如果条件结果是false，程序的当前状态就会变成无效，代码执行终止并且应用会直接退出。

你可以使用断言和先决条件来表达出你做出的假设或者你编写代码时的预期结果，因此你可以把它包含进你的程序中作为代码的一部分。断言会帮助你在开发过程中找出错误以及对代码结果不正确的假设。先决条件会帮助你在生产环境中检测问题。

除了在运行时验证你的期望，断言和先决条件还可以成为代码中有用的文档清单。不像错误处理中讨论的错误条件那样，断言和先决条件不能用来处理可恢复的或者期望的错误。因为失败的断言和先决条件意味着程序状态的无效，没有办法可以捕捉这种失败的断言。

使用断言和先决条件并不是要去替代当条件无效时就不去执行代码的设计。但是，使用它们可以在无效状态发生时，能够强制执行有效数据和状态来使应用程序更容易终止，这样就会帮助问题更容易被调试出来。无效状态一被检测出来就终止执行也会帮助减少由无效状态引起的破坏。

断言和先决条件的不同点在于它们什么时候会被检查： 断言仅仅在调试模式中会被检查，而先决条件在调试和生产两种模式下都会检查。在生产构建模式中，断言内的条件不会被检查。这意味着你可以在开发过程中使用任意多的断言而不会影响生产模式的表现。

#### 用断言调试
你可以通过调用Swift标准函数库中的` assert(_:_:file:line:)`函数来写一个断言。
这个函数的参数是一个结果为true或者false的表达式和一个展示条件结果为false时的消息。例如：
```
let age = -3
assert(age >= 0, "A person's age can't be less than zero.")
// This assertion fails because -3 is not >= 0.
```

在这个例子中，如果`age >= 0`的结果是true（即age是非负数），那么代码就会继续执行。如果age的值是负数，上面代码中`age >= 0`的结果就是false，断言失败，程序终止。

你可以忽略断言消息---例如，当它只是之前断言的重复时：
```
assert(age >= 0)
```

如果代码已经检查过条件了，你可以用`assertionFailure(_:file:line:) `函数来表明断言失败，例如：
```
if age > 10 {
    print("You can ride the roller-coaster or the ferris wheel.")
} else if age >= 0 {
    print("You can ride the ferris wheel.")
} else {
    assertionFailure("A person's age can't be less than zero.")
}
```


#### 强制先决条件
无论什么时候，只要一个条件有可能是false，那么就可以使用先决条件，但是一定要是true的时候才能继续执行你的代码。
例如，使用先决条件来来检查下表是否越界，或者检查函数所传递的值是否有效。

你可以通过调用`precondition(_:_:file:line:)`函数来写一个先决条件。这个函数的参数是一个结果为true或者false的表达式和一个展示条件结果为false时的消息。例如：
```
// In the implementation of a subscript...
precondition(index > 0, "Index must be greater than zero.")
```

当然你也可以调用`preconditionFailure(_:file:line:)`来表明失败已经发生---例如，如果一个switch语句的默认分支被执行，但是所有有效数据其实应该被switch的其他分支中的一个进行处理。

```
注意
如果你使用未检查(-Ounchecked)模式进行编译，先决条件是不会被检查的。编译器此时会默认所有先决条件总是true，并且相应地它会优化你的代码。
然而，无论优化设置如何，fatalError(_:file:line:)函数总是会终止程序的执行。
你可以在做原型设计和早期开发过程中使用fatalError(_:file:line:)函数来创建一些代码桩来代表这里暂时还未实现，写法可以是'fatalError("Unimplemented")'。
因为致命错误永远也不会被优化器省略掉，所以不像断言和先决条件，你可以确保当程序遇到桩时执行就会终止。
```



