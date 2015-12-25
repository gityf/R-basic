# 1. R用#注释
    \#this is comment.

# 2. 赋值
    x <- 11
    y <- 3.14
    t <- TRUE
    f <- FALSE
    str <- "this is string"

# 3.向量
# 一个向量里面只能包含同一类型的对象
## 创建向量
    x <- vector("character", length=10)
    x <- 1:4
    y <- c(1,2,33,4)
    y1 <- c(TRUE, 10, "aa")
    y2 <- c("bb", "cc", "aa")

## 强制类型转换
    as.numeric(x)
    as.logical(x)
    as.character(x)
