## 语言指南


### 基础

Swift是一个开发iOS, macOS, watchOS和tvOS应用的新编程语言。尽管是新语言，如果你有C和Objective-C语言的开发经验，那么对Swift很多地方都会比较熟悉。
swift对所有C系和Objective-C的类型实现了自己的版本，包括`Int`代表整数，`Double`和`Float`代表浮点数，`Bool`代表布尔值，`String`代表文本数据。Swift也在[集合类型中]()中提供了三种主要集合类型的功能强大的实现，包括`Array`, `Set`和`Dictionnary`。

和C语言一样，Swift也使用变量名标识一个变量来存储和指向一个值。Swift中也大量使用了值不会改变的常量，并且比C语言中的常量功能更加强大, 当你使用的值不需要改变时，使用常量会更加安全和简洁。

除了熟悉的类型，Swift还提供了Objective-C中没有的类型，比如元组。元组允许你创建和传递一组变量值。比如一个函数可以把多个值组合成一个元组作为一个单一混合值返回。

Swift还提供了可选类型，可选类型变量允许没有值。也就是说可选变量要么有一个等于x的值，要么不等于任何值。可选类型类似于Objective-C中的空指针nil，但是Swift中可以用于所有类型，不仅局限在类。可选类型不仅更加安全，而且比Objective-C中的空指针nil使用得更广泛，它是Swift中许多强大特性的基石。

Swift是一种类型安全的语言，这就意味着语言可以帮助提示你所写的代码变量的类型。比如如果你的代码需要一个`String`类型的变量, 类型安全会阻止你错误地传递一个`Int`类型的变量。同样的，如果你的代码需要一个非可选类型的`String`变量，类型安全也会阻止你传一个可选类型的`String`变量，它会在开发过程中尽可能早地帮你捕捉到并且修复掉错误。
