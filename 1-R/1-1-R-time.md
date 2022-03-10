# R时间

## 1. 日期

### 1.1 获取当前日期

```R
Sys.Date()
```

### 1.2 把字符串转换为日期

当格式为`%Y-%m-%d`、`%Y/%m/%d`时：

```R
as.Date("2022-03-10")
as.Date("2022/03/10")
```

自定义格式：

```R
as.Date("22-03-10", "%y-%m-%d")
```

### 1.3 日期求差

例1，计算生存时间：

```R
last_followup_date <- as.Date("1997/8/29")
date_of_surgery <- as.Date("1996/12/17")
os_time_days <- as.integer(difftime(
    last_followup_date,
    date_of_surgery,
    units = "days"
))
```

例2，计算年龄（不是100%精确）：

```R
calc_age <- function(now = Sys.Date(), birthday) {
    if (is.character(birthday)) {
        birthday <- as.Date(birthday)
    }
    if (is.character(now)) {
        now <- as.Date(now)
    }
    days <- as.integer(difftime(now, birthday, units = "days"))
    floor(days / 365)
}
```

## 2. 时间

### 2.1 获取当前时间

```R
Sys.time()
```
