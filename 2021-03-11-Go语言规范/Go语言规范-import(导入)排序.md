# Go语言规范-import(导入)排序

当我们需要通过 import 导入一些包时，如何进行排序呢？

> 建议顺序：标准库，系统库，第三方库，本项目库，不同分组使用空行分割开。

#### Bad

```go
import (
        "database/sql"
        "io"
        "strconv"
        "golang.org/x/net/context"
        "example.com/foo/bar"
        "example.com/foo/baz"
    )
```

#### Good

```go
import (
        "database/sql"
        "io"
        "strconv"

        "golang.org/x/net/context"

        "example.com/foo/bar"
        "example.com/foo/baz"
    )
```

**参考文章：**

https://stackoverflow.com/questions/38704769/golang-import-grouping-by-package

https://github.com/uber-go/guide/blob/master/style.md#import-aliasing