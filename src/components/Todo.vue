<template>
  <div>
    <div class="table">
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
.table{
  margin: 0 20px;
}
.table-body {
  max-height: 400px;
  overflow-y: scroll;
}

.table-header {
  display: flex;
  position: sticky;
}

.table-row {
  display: flex ;
  padding : 10px ;
  background : transparent ;
  border: 1px solid transparent;
}

.table-row:hover {
  border: 1px solid grey;
}

.name { 
  flex : 2;
  display: flex ;
  justify-content: center;
  text-align: center;
}

.price {
  flex : 1; 
  text-align: center;
}

.hour-change {
  flex : 2;
  text-align: center;
}

.red {
  color  : red ;
}

.green {
  color : green ;
}

/* width */
::-webkit-scrollbar {
  width: 4px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1; 
}
 
/* Handle */
::-webkit-scrollbar-thumb {
  background: rgb(105, 123, 224); 
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: rgb(79, 99, 212); 
}

</style>

