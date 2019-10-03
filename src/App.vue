<template>
  <div id="app">
    <label>请输入日期</label><input type="text" @keyup="handleKeyUp($event)">
    <div v-show="date" class="date-info">{{ inputDate.toDateString() }}</div>
    <Calender :date="date"
    :inputDate = "inputDate"
    @goToLastYear="gotolastYear"
    @goToNextYear="gotonextYear"
    @goToLastMonth="gotolastMonth"
    @goToNextMonth="gotoNextMonth"/>
  </div>
</template>

<script>
import Calender from './components/Calender'

export default {
  name: 'App',
  components: {
    Calender
  },
  data () {
    let date = new Date()
    return {
      date: new Date(date.getFullYear(), date.getMonth(), date.getDate()),
      inputDate: new Date()
    }
  },
  methods: {
    handleKeyUp (e) {
      if (e.keyCode === 13) {
        // 处理输入框输入的日期;
        let date = new Date(e.target.value)
        if (date.toString() === 'Invalid Date') {
          alert('请正确格式的日期(年/月/日)')
        } else {
          this.inputDate = date
        }
        e.target.value = ''
      }
    },
    gotolastYear () {
      this.inputDate = new Date(this.inputDate.getFullYear() - 1, this.inputDate.getMonth(), this.inputDate.getDate())
    },
    gotonextYear () {
      this.inputDate = new Date(this.inputDate.getFullYear() + 1, this.inputDate.getMonth(), this.inputDate.getDate())
    },
    gotolastMonth () {
      var currentMonth = this.inputDate.getMonth()
      if (currentMonth === 0) {
        this.inputDate = new Date(this.inputDate.getFullYear() - 1, 11, 1)
      } else {
        this.inputDate = new Date(this.inputDate.getFullYear(), currentMonth - 1, 1)
      }
    },
    gotoNextMonth () {
      var currentMonth = this.inputDate.getMonth()
      if (currentMonth === 12) {
        this.inputDate = new Date(this.inputDate.getFullYear() + 1, 0, 1)
      } else {
        this.inputDate = new Date(this.inputDate.getFullYear(), currentMonth + 1, 1)
      }
    }
  }
}
</script>

<style>
#app {
margin: 0 auto;
width: 370px;
height: 500px;
padding: 10px;
background:#c7f0db ;
color:#464159;
}
#app .date-info{
  text-align: center
}
#app input{
  text-indent: 20px;
}
</style>
