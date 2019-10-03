# vue-calender

> A vue-calender project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

## 实现功能
1 生成当月的日历，并且标记当天的日期
2 在输入框中输入日期会跳转到对应的月份，并标记输入的日期
3 中间两个按钮( < >)控制月份的更改，可以切换月份
4 旁边两个按钮( << >>)控制月份的更改，可以切换年份

### 日历生成的核心算法
获取某一日期：计算日期当月的第一天(firstDate)和当月的最后一天(lastDate)
计算日历开始的位置 startPos：firstDate.getDay()-1
计算当月的总天数 totalDays：lastDate.getDate()
计算存放日期的行数 rows ：Math.ceil((startPos +totalDay)/7)
需要的总格子数totalItems :rows*7

### 月份切换
上一个月 gotolastMonth:将当前日期的月份减一，当month<0 时 let month = 11
下一个月 gotonextMonth:将当前日期的月份加一，当month==12 时 let month = 0

