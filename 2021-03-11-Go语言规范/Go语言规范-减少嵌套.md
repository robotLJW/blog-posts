# Go语言规范-减少嵌套

代码应该尽可能减少嵌套，在处理错误/特殊情况时，需提前返回或继续循环，不要超过4层！

**Bad**

```go
for _, v := range data {
  if v.F1 == 1 {
    v = process(v)
    if err := v.Call(); err == nil {
      v.Send()
    } else {
      return err
    }
  } else {
    log.Printf("Invalid v: %v", v)
  }
}
```

**Good**

```go
for _, v := range data {
  if v.F1 != 1 {
    log.Printf("Invalid v: %v", v)
    continue
  }

  v = process(v)
  if err := v.Call(); err != nil {
    return err
  }
  v.Send()
}
```

参考资料：

https://github.com/uber-go/guide/blob/master/style.md#function-names