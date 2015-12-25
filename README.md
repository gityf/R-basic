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
#4.数组
    #创建4行6列的2维数组
    ax <- array(1:24, dim=c(4,6))
    #创建2行3列4维的数组
    ax1 <- array(1:24, dim=c(2,3,4))
    > ax
         [,1] [,2] [,3] [,4] [,5] [,6]
    [1,]    1    5    9   13   17   21
    [2,]    2    6   10   14   18   22
    [3,]    3    7   11   15   19   23
    [4,]    4    8   12   16   20   24
    > ax1
    , , 1

         [,1] [,2] [,3]
    [1,]    1    3    5
    [2,]    2    4    6

    , , 2

         [,1] [,2] [,3]
    [1,]    7    9   11
    [2,]    8   10   12

    , , 3

         [,1] [,2] [,3]
    [1,]   13   15   17
    [2,]   14   16   18

    , , 4

         [,1] [,2] [,3]
    [1,]   19   21   23
    [2,]   20   22   24
#5.列表
    #可以包含不同的元素
    l <- list(1, 4, TRUE, "cc", 10L, 4+2i)
    #命名列表
    l2 <- list(a=1,b=2,cc=23)
    #创建2个向量元素的列表
    l3 <- list(c(2,1,4), c(4,7,8))
    #用列表给矩阵设置维度名称
    mx <- matrix(10:15, nrow = 3, ncol = 2)
    dimnames(mx) <- list(c("x","y","z"),c("h","w"))
        > l
        [[1]]
        [1] 1

        [[2]]
        [1] 4

        [[3]]
        [1] TRUE

        [[4]]
        [1] "cc"

        [[5]]
        [1] 10

        [[6]]
        [1] 4+2i

        > l2
        $a
        [1] 1

        $b
        [1] 2

        $cc
        [1] 23

        > mx
           h  w
        x 10 13
        y 11 14
        z 12 15
        > l3
        [[1]]
        [1] 2 1 4

        [[2]]
        [1] 4 7 8
#因子factor
    用于处理分类数据（处理有序和无序的分类数据）
    相当于一个整数向量+标签
    y <- factor(c("f","f","t","t","f"), levels=c("t","f"))
    levels用于设置基线水平
    #去掉因子的属性
    unclass(y)
    > y
    [1] f f t t f
    Levels: t f
    > table(y)
    y
    t f 
    2 3 
    > unclass(y)
    [1] 2 2 1 1 2
    attr(,"levels")
    [1] "t" "f"
    > class(unclass(y))
    [1] "integer"


#缺失值
    NA/NaN: NaN是NA的子集,NA有类型属性：integer NA,character NA etc.
    判断是否是缺失值
    is.na()
    is.nan()
    x <- c(1,2,NA,4,NA)
    is.na(x)
    is.nan(x)
    x <- c(1,2,NaN,4,NaN)
    is.na(x)
    is.nan(x)
    ######
    > x <- c(1,2,NA,4,NA)
    > is.na(x)
    [1] FALSE FALSE  TRUE FALSE  TRUE
    > is.nan(x)
    [1] FALSE FALSE FALSE FALSE FALSE
    > x <- c(1,2,NaN,4,NaN)
    > is.na(x)
    [1] FALSE FALSE  TRUE FALSE  TRUE
    > is.nan(x)
    [1] FALSE FALSE  TRUE FALSE  TRUE
