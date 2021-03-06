## 关于Swift


无论是在手机、桌面、服务端还是其他编程场景，使用Swift都是一种优雅的软件编写方式。它是一种安全、快速的交互式编程语言，它凝聚着来自苹果工程师文化和它的开源社区贡献来的对现代编程语言的思考。编译器为性能优化过，语言为开发便利优化过，二者都没有妥协。

Swift对刚入门编程的人很友好。它是一门工业生产级的编程语言同时编写体验又像是一门脚本语言。在Playground中编写Swift代码可以实现所见即所得而无需提前构建和运行应用。

Swift在采纳了现代编程规范的基础上定义了大量的通用编程错误提示：
+ 变量在使用前总是需要初始化。
+ 数组和切片会执行越界检查。
+ 整数会执行溢出检查。
+ 可选类型变量要确保`nil`值会被显式处理。
+ 内存是自动管理的。
+ 错误处理允许从意外故障中进行受控恢复。

Swift代码编译优化后可以最大化利用现代硬件的性能。它的语法和标准库是基于先进的规则设计而来，这使得用简单的方法写出来的代码就可以发挥最好的性能。对安全和速度两方面的结合让Swift成为了无论是编写“Hello, world”还是整个操作系统都是不错的选择。

Swift结合了强大的类型推断和由现代化轻量级的语法带来的模式匹配，允许用一种清晰且简洁的方式实现复杂的功能。因此，代码不仅容易编写而且也方便阅读和维护。

Swift是历经多年研发而出的成果，它将继续演进以吸纳新的特点并保持兼容。我们对Swift的目标是很远大的，现在我们已经迫不及待地想看看你可以利用它来创造些什么了。


### 版本兼容性

本书介绍的Swift版本是5.3，这也是Xcode 12中的Swift默认版本。你可以使用Xcode 12来构建用Swift 5.3，Swift 4.2或者Swift 4编写的`target`。

***
当你使用Xcode 12来构建Swift 4和4.2的代码时，大部分5.3的功能也是可用的。但尽管如此，以下的变化只能在用Swift 5.3或更高版本编写的代码中可用：
+ 返回不透明类型的函数依赖于Swift 5.1的runtime.
+ try语句不会为已经返回可选类型的表达式引入额外级别的可选性。
+ 大整数的初始化表达式会被推断为正确的整数类型。例如，`UInt64(0xffff_ffff_ffff_ffff)`的结果为正确的值而不是溢出。

用Swift 5.3编写的`target`可以依赖于用4.2或者4编写的`target`，反之亦然。也就是说，如果你有一个大的项目，被分成了多个`framework`, 那么你可以一次性把一个`framework`的代码由Swift 4迁移到Swift 5.3。