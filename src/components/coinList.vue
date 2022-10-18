<template>
    <div>
     
      <div class="table">
  
        <div class="table-header">
          <div class="name">Name</div>
          <div class="price">Price</div>
          <div class="hour-change">24 H Change</div>
        </div>
        <div class="table-body">
        <div class="table-row" v-for="(todo, index) in Alltodos" :key="index">
          <div class="name">
            <img ng-src="{{todo.ImageUrl}}" alt="coin logo" />
            <div>
              {{todo.Name}}
            </div>
          </div>
          <div class="price">{{todo.Price}}</div>
          <div :class="todo.HCHANGE > 0 ? 'hour-change green' : ' hour-change red'">{{todo.HCHANGE}} %</div>
        </div>
        </div>
      </div>
    </div>
  </template>
  
  <script >
  import { ref } from "vue";
  import axios from "axios";
  
  export default {
    name: "Todo",
    components: {
    },
    setup() {
      let Alltodos = ref([]);
      const API_URL =
        "https://min-api.cryptocompare.com/data/top/totaltoptiervolfull?limit=20&tsym=USD&api_key=96b3cbe243ed487e78905885dd0ddb7084b2ee60ffb942ffa07ffb24cf8f70eb";
  
      const getTodos = () => {
        axios
          .get(API_URL)
          .then((response) => {
            console.log(response.data["Data"]);
            const tempCoinlist = response.data["Data"];
            let coinId = 0;
            tempCoinlist.forEach((coin) => {
              Alltodos.value.push({
                ID: coinId,
                Name: coin["CoinInfo"]["Name"],
                ImageUrl: coin["CoinInfo"]["ImageUrl"],
                Price: coin["DISPLAY"].USD.PRICE,
                HCHANGE: (
                  (parseFloat(coin["DISPLAY"].USD.CHANGE24HOUR.replace("$", "")) /
                    parseFloat(coin["DISPLAY"].USD.PRICE.replace("$", "")))
                ).toPrecision(4),
                // HCHANGE: (
                //   (parseFloat(coin["DISPLAY"].USD.CHANGE24HOUR.replace("$", "")) /
                //     parseFloat(coin["DISPLAY"].USD.PRICE.replace("$", ""))) *
                //   100
                // ).toPrecision(4),
              });
            });
            console.log("", Alltodos);
          })
          .catch((error) => {
            console.log("error", error);
          });
      };
      //api call to retrieve all todos
      getTodos();
  
    
      return {
        Alltodos,
      };
    },
  };
  </script>
  
  
  <style scoped>
  .table{
    margin: 0 20px;
    padding: 20px 0;
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
  