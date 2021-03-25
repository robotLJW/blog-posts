# Go语言规范-没有必要的else

如果在 if 的两个分支中都设置了变量，则可以用单个 if 替换它。

**Bad**

```go
var a int
if b {
  a = 100
} else {
  a = 10
}
```

**Good**

```go
a := 10
if b {
  a = 100
}
```

**参考材料:**

https://github.com/uber-go/guide/blob/master/style.md#unnecessary-else