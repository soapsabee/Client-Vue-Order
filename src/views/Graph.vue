<template>
  <div v-if="datasets[0].data.length > 0" id="app">
    <chartjs-bar v-bind:labels="labels" v-bind:datasets="datasets" v-bind:option="option"></chartjs-bar>
  </div>
</template>

<script>
import axios from "axios"
export default{
  data() {
    return {
      labels :[],
      datasets:[
        {
          label: '# ปริมาณ Order ของ ลูกค้า',
          data: [],
          backgroundColor: ["Red","Yellow","Purple"]
        }
      ],
        option: {
          title:{
            display:true,
            position:"bottom",
            text:"ชื่อลูกค้า"
          }
        }
    }
  },
  mounted(){
      var instance = this.labels;
      var num = this.datasets[0].data;
  axios.get("https://afternoon-sands-15941.herokuapp.com/api/report")
  .then(function(response){
    response.data.data.map((posts) => {
    instance.push(posts.customer_id)
    num.push(posts.count)
    console.log(posts.title)
    
    })
    
  })
}
}

</script>