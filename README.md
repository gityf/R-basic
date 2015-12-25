# R-basic
R lang basic note.
# 1. R用#注释
    #this is comment.

# 2. 赋值
    x <- 11
    y <- 3.14
    t <- TRUE
    f <- FALSE
    str <- "this is string"

# 3.向量
    一个向量里面只能包含同一类型的对象
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
#3.矩阵
    #创建3行，2列的矩阵，依次赋值10到15
    mx <- matrix(10:15, nrow = 3, ncol = 2)
    #创建一个向量
    y1 <- c(1,2,3,4,5,6)
    #将向量转成3行2列的矩阵
    dim(y1) <- c(3,2)
    #将两个矩阵行拼接
    rbind(mx,y1)
    #将两个矩阵列拼接
    cbind(mx,y1)
    > rbind(mx,y1)
         [,1] [,2]
    [1,]   10   13
    [2,]   11   14
    [3,]   12   15
    [4,]    1    4
    [5,]    2    5
    [6,]    3    6
    > cbind(mx,y1)
         [,1] [,2] [,3] [,4]
    [1,]   10   13    1    4
    [2,]   11   14    2    5
    [3,]   12   15    3    6
