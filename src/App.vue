<template>
  <div id="app">
    <Header :text="header" />
    <div class="content-main">
      <Card v-for="item in catFood" :key="item.description" :model="item"/>
    </div>
  </div>
</template>

<script>
  import Header from './components/Header'
  import Card from './components/Card'

export default {
  name: 'app',
  components: {
    Card,
    Header
  },
  data(){
    return {
      header: 'Ты сегодня покормил кота?',
      catFood: [
        {
          id: 0,
          description: 'Печень утки разварная с артишоками.',
          taste: 'с фуа-гра',
          gift: '<b>10</b> порций мышь в подарок',
          qty: '0,5',
        },
        {
          id:1,
          description: 'Головы щучьи с чесноком да свежайшая сёмгушка.',
          taste: 'с рыбой',
          gift: '<b>40</b> порций <b>2</b> мыши в подарок',
          qty: '2',
        },
        {
          id: 2,
          description: 'Филе из цыплят с трюфелями в бульоне.',
          taste: 'с курой',
          gift: '<b>100</b> порций <b>5</b> мышей в подарок<br/>заказчик доволен',
          qty: '5',
        }
      ]
    }
  }
}
</script>

<style lang="less">
  @import "styles/main.less";
</style>
