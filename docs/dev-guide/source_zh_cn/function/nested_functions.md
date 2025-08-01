# 嵌套函数

定义在源文件顶层的函数被称为全局函数。定义在函数体内的函数被称为嵌套函数。

使用范围：

- 嵌套函数的作用域仅限于其所在的外部函数。嵌套函数可以访问外部函数的变量和参数，但外部函数不能直接访问嵌套函数的内部变量。
- 嵌套函数可以被外部函数调用，也可以被外部函数返回。

生命周期：

- 嵌套函数的生命周期与外部函数紧密相关。每次外部函数调用时，嵌套函数被创建；外部函数执行完毕后，嵌套函数通常被销毁，除非通过返回或闭包被外部引用。

使用规则和注意事项：

- 仅在对应外部函数中使用嵌套函数。
- 避免过度嵌套。这会使代码结构变得复杂，难以理解和维护，因此避免过多嵌套导致代码混乱。
- 注意闭包的使用。如果嵌套函数被返回并作为闭包使用，需要注意闭包可能会捕获外部函数的变量，导致外部函数的变量在外部函数结束后仍然被占用，从而影响内存管理。

示例，函数 `foo` 内定义了一个嵌套函数 `nestAdd`，可以在 `foo` 内调用该嵌套函数 `nestAdd`，也可以将嵌套函数 `nestAdd` 作为返回值返回，在 `foo` 外对其进行调用：

<!-- verify -->

```cangjie
func foo() {
    func nestAdd(a: Int64, b: Int64) {
        a + b + 3
    }

    println(nestAdd(1, 2))  // 6

    return nestAdd
}

main() {
    let f = foo()
    let x = f(1, 2)
    println("result: ${x}")
}
```

程序会输出：

```text
6
result: 6
```
