<template>
  <div id="app">

    <!-- input输入框 -->
    <div class="item">
      <div class="input-box">
        <Input type="text" v-model="text" placeholder="请输入内容" clearable />
      </div>
      <p>{{text}}</p>
    </div>
    <!-- 手风琴 -->
    <div class="item">
      value:{{activeNames}}
      <Collapse v-model="activeNames" :accordion="accordion">
        <CollapseItem title="十六客服的结果" name="1">
          <p>sldkjfalskdjflaiwrgoawvr</p>
          <p>sldkjfalskdjflaiwrgoawvr</p>
          <p>sldkjfalskdjflaiwrgoawvr</p>
          <p>sldkjfalskdjflaiwrgoawvr</p>
          <p>sldkjfalskdjflaiwrgoawvr</p>
        </CollapseItem>
        <CollapseItem title="收费的噶" name="2">
          <p>手动阀撒发射点发违法</p>
          <p>阿嘎尔办法俄铝阿尔高</p>
          <p>阿嘎尔办法俄铝阿尔高</p>
        </CollapseItem>
        <CollapseItem title="爱人哈巴var给" name="3">
          <p>个图巴尔v热热本特纳</p>
          <p>藤为逃避问题</p>
        </CollapseItem>
      </Collapse>
    </div>
    <!-- 星级评分 -->
    <div class="item">
      <span>star：{{rateValue}}</span>
      <Rate v-model="rateValue"></Rate>
    </div>
    <!-- 滑块 -->
    <div class="item">
      {{slider}}
      <button @click="handeAddClick">Add</button>
      <Slider v-model="slider"></Slider>
    </div>
    <!-- Popover -->
    <div class="item">
      <Popover title="标题" width="200">
        <div>12345</div>
        <button slot="reference">Popover</button>
      </Popover>
    </div>
    <!-- 时间选择框 -->
    <div class="item">
      timePicker:
      <TimePicker v-model="time"></TimePicker>
    </div>
    <div class="item">
      timepicker-selectableRange:
      <TimePicker v-model="time" selectableRange></TimePicker>
    </div>
    <!-- 级联 -->
    <div class="item">
      <Cascader ></Cascader>
    </div>
    <!-- 日历 -->
    <div class="item">
      <p>{{date}}</p>
      <div class="calendar">
        <Calendar v-model="date" first-day="1">
          <template v-slot="scope">{{scope.data.month+'-'+scope.data.day}}</template>
        </Calendar>
      </div>
    </div>

  </div>
</template>

<script>
import Calendar from '@/components/calendar'
import Input from '@/components/input'
import Collapse from '@/components/collapse/collapse'
import CollapseItem from '@/components/collapse/collapse-item'
import Rate from '@/components/rate'
import Slider from '@/components/slider'
import TimePicker from '@/components/timePicker'
import Popover from '@/components/popover'
import Cascader from '@/components/cascader'

export default {
  name: 'App',
  components: {
    Calendar,
    Input,
    Collapse,
    CollapseItem,
    Rate,
    Slider,
    TimePicker,
    Popover,
    Cascader
  },
  data () {
    return {
      date: '2020 07 17',
      firstDay: 2, // 0~6  => 周日到周六
      rateValue: 3,
      text: '',
      activeNames: ['1', '3'],
      accordion: true,
      slider: 30,
      time: ''
    }
  },
  methods: {
    handeAddClick () {
      this.slider++
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '//at.alicdn.com/t/font_1503790_yp9803cj1bg.css';
#app
  // height 5000px
  overflow auto
  height 100%
.item {
  margin: 20px;
  padding: 20px;
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);

  .calendar {
    height: 500px;
    width: 600px;
  }

  .input-box {
    margin-top: 10px;
  }
}
</style>
