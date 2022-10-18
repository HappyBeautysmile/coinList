<template>
  <div>
    <div class="main">
      <LineChart />
      <coinList/>
    </div>
  </div>
</template>

<script >
import LineChart from './lineChart.ts'
import coinList from '@/components/coinList'

export default {
  name: "Todo",
  components: {
    LineChart,
    coinList
  },
};
</script>
<style scoped>
.main{
  padding : 120px;
}
</style>  

