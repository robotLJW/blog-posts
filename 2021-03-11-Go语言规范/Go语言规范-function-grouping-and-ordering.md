# Go语言规范-Function Grouping and Ordering

如下代码：大家对 const，var，struct排序应该是没有太大异议，放在最上头即函数的上面。

> go语言的函数和方法是两个不同的东西，方法是包含接受者的函数，如 `func (s *something) Cost() {...}`

```go
type something struct{ ... }

const(
    a = xx
    b = xx
)

var (
	xxx  = 1
    xxxx = 2
)

func (s *something) Cost() {
  return calcCost(s.weights)
}

func calcCost(n []int) int {...}

func (s *something) Stop() {...}

func newSomething() *something {
    return &something{}
}
```

**那么函数(包含接受者的函数)分组和排序呢？**

1. 按粗略的调用顺序排序
2. 文件中的函数应按接收者分组

建议顺序：

1. const，var，struct定义
2. newABC/NewABC
3. 接受者函数
4. 函数

```go
type something struct{ ... }

const(
    a = xx
    b = xx
)

var (
	xxx  = 1
    xxxx = 2
)

func newSomething() *something {
    return &something{}
}

func (s *something) Cost() {
  return calcCost(s.weights)
}

func (s *something) Stop() {...}

func calcCost(n []int) int {...}
```

**参考资料:**

https://github.com/uber-go/guide/blob/master/style.md#function-names