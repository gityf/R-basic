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
#数据框
    #创建数据框，每个元素是一列 列名=列内容格式
    > df <- data.frame(id = c(1,2,3,4), name=c("zhangsan", "lisi","wangwu","maliu"), age=c(10,20,30,40))
    > #获取有多少行
    > nrow(df)
    [1] 4
    > #获取有多少列
    > ncol(df)
    [1] 3
    > data.matrix(df)
         id name age
    [1,]  1    4  10
    [2,]  2    1  20
    [3,]  3    3  30
    [4,]  4    2  40
#日期和时间
    > date()
    [1] "Fri Dec 25 14:03:00 2015"
    > x <- date()
    > class(x)
    [1] "character"
    > x2 <- Sys.Date()
    > x2
    [1] "2015-12-25"
    > class(x2)
    [1] "Date"
    > x3 <- as.Date(2015-12-12)
    Error in as.Date.numeric(2015 - 12 - 12) : 'origin'一定得给值
    > x3 <- as.Date("2015-12-12")
    > x3
    [1] "2015-12-12"
    > weekdays(x3)
    [1] "星期六"
    > months(x3)
    [1] "十二月"
    > quarters(x3)
    [1] "Q4"
    > julian(x3)
    [1] 16781
    attr(,"origin")
    [1] "1970-01-01"
    > x
    [1] "Fri Dec 25 14:03:19 2015"
    > 
    > y = Sys.time()
    > y
    [1] "2015-12-25 14:06:48 CST"
    > class(y)
    [1] "POSIXct" "POSIXt" 
    > p <- as.POSIXlt(y)
    > p
    [1] "2015-12-25 14:06:48 CST"
    > class(p)
    [1] "POSIXlt" "POSIXt" 
    > names(unclass(p))
     [1] "sec"    "min"    "hour"   "mday"   "mon"    "year"  
     [7] "wday"   "yday"   "isdst"  "zone"   "gmtoff"
    > p$sec
    [1] 48.9366
    > p$min
    [1] 6
    > p$year
    [1] 115
    > p$wday
    [1] 5
    > p$mon
    [1] 11
    > p$hour
    [1] 14
