<template>
  <div :class="{ 'calender-item':true, currentDay: isCurrentDay }"
  >
    {{ day}}
  </div>
</template>

<script>
export default { // 日期小方块
  name: 'CalenderItem',
  props: ['item', 'currentDay'],
  computed: {
    day () { // 计算日期
      if (this.item) {
        return this.item.getDate()
      } else {
        return ''
      }
    },
    isCurrentDay () { // 判断是不是输入的日期
      return this.currentDay.toString() === this.item.toString()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calender-item{
  float: left;
  width: 50px;
  height: 50px;
  line-height: 50px;
  text-align: center;
  border: 1px solid  #8bbabb;
}
.currentDay{
  background: #f9d5bb
}
</style>
