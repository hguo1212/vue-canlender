<template>
  <div :class="{ 'calender-item':true, currentDay: isCurrentDay }"
  >
    {{ day>0 ? day : '' }}
  </div>
</template>

<script>
export default {
  name: 'CalenderItem',
  props: ['item', 'currentDay'],
  computed: {
    day () {
      if (this.item) {
        return this.item.getDate()
      } else {
        return 0
      }
    },
    showToday () {
      return this.day > 0
    },
    isCurrentDay () {
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
