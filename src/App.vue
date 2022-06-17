<template>
  <div id="app">
    <StatusButton />
    <StatusButton>
      <template v-slot:buttontext>
        <p 
          class="buttonheader" 
          :data="statusDataList" > 
          {{statusDataList.button?.caption}}
        </p>
      </template>
      <template v-slot:status1>
        <p  
          class="topleft"
          :data="statusDataList"
          :style="{'background-color': statusDataList.status1?.colour}">   
          {{statusDataList.status1?.caption}}
        </p>
      </template>
      <template v-slot:status2>
        <p  
          class="topright"
          :data="statusDataList"
          :style="{'background-color': statusDataList.status2?.colour}">   
          {{statusDataList.status2?.caption}}
        </p>
      </template>
      <template v-slot:status3>
        <p  
          class="bottomleft"
          :data="statusDataList"
          :style="{'background-color': statusDataList.status3?.colour}">   
          {{statusDataList.status3?.caption}}  
        </p>
      </template>
      <template v-slot:status4>
        <p  
          class="bottomright"
          :data="statusDataList"
          :style="{'background-color': statusDataList.status4?.colour}">   
          {{statusDataList.status4?.caption}} 
        </p>
      </template>
    </StatusButton>
  </div>
</template>

<script>
import StatusButton from './components/StatusButton.vue'
//import axios from "axios"

export default {
  name: 'app',
  components: {
    StatusButton,
  },
   data() {
    return {
      statusDataList: {},
    }
  },
  methods: {
    getStatusData() {
      fetch("https://mocki.io/v1/9884a9b3-8aa2-461b-9339-da1cc08adcfa")
        .then(response => response.json())
        .then(data => (this.statusDataList = data))  
    },
  },
  created() {
    this.getStatusData()
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
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
  background-color: white;
  color: black;
}
.notification .topleft {
  position: absolute;
  top: 10px;
  left: 10px;
  padding: 10px 10px;
  border-radius: 20px;
  border: 1px solid black;
  background-color: white;
  color: black;
}
.notification .bottomright {
  position: absolute;
  bottom: 10px;
  right: 10px;
  padding: 10px 10px;
  border-radius: 20px;
  border: 1px solid black;
  background-color: white;
  color: black;
}
.notification .bottomleft {
  position: absolute;
  bottom: 10px;
  left: 10px;
  padding: 10px 10px;
  border-radius: 20px;
  border: 1px solid black;
  background-color: white;
  color: black;
}
</style>