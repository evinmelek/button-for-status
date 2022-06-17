<template>
  <div> 
    <button class="notification" @click="status1(); status2(); getStatusData();" style="background: url(image.png)">
      <div v-for="statusData in statusDataList" :key="statusData">
           
          <slot name="buttontext"></slot>
          <slot name="status1"></slot>
          <slot name="status2"></slot>
          <slot name="status3"></slot>
          <slot name="status4"></slot>
      </div> 
    </button>
  </div>
</template>

<script>
import axios from "axios"
export default {
  name: "StatusButton",
  data() {
    return {
      statusDataList: {}
    };
  }, 
  methods: {
    getStatusData() {
      axios.get("https://mocki.io/v1/9884a9b3-8aa2-461b-9339-da1cc08adcfa")
        .then(response => response)
        .then(data => (this.statusDataList = data)) 
    },
    status1(){
      axios.get("https://mocki.io/v1/9884a9b3-8aa2-461b-9339-da1cc08adcfa")
        .then(response => response)
        .then(data => (this.statusDataList = data))
      console.log("status1")       
    },
    status2(){
      axios.get("https://mocki.io/v1/9884a9b3-8aa2-461b-9339-da1cc08adcfa")
        .then(response => response)
        .then(data => (this.statusDataList = data))   
      console.log("status2")
    }
  },
};
</script>

<style scoped>
body {
  font-family: Arial, Helvetica, sans-serif;
}

.notification {
  background-color: #555;
  color: white;
  text-decoration: none;
  height: 200px;
  width: 400px;
  margin-top: 30px;
  margin-bottom: 30px;
  padding: 15px 26px;
  position: relative;
  display: inline-block;
  border-radius: 20px;
  opacity: 0.8;
}

.notification:hover {
  opacity: 1;
}
.notification .buttonheader{
  position: absolute;
  top: 80px;
  right: 140px;
  padding: 10px 10px;
  border-radius: 20px; 
  color: black;
}

.notification .topright {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 10px 10px;
  border-radius: 20px;
  border: 1px solid black; 
  color: black;
}
.notification .topleft {
  position: absolute;
  top: 10px;
  left: 10px;
  padding: 10px 10px;
  border-radius: 20px;
  border: 1px solid black; 
  color: black;
}
.notification .bottomright {
  position: absolute;
  bottom: 10px;
  right: 10px;
  padding: 10px 10px;
  border-radius: 20px;
  border: 1px solid black; 
  color: black;
}
.notification .bottomleft {
  position: absolute;
  bottom: 10px;
  left: 10px;
  padding: 10px 10px;
  border-radius: 20px;
  border: 1px solid black; 
  color: black;
}
</style>