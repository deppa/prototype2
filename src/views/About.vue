<template>
  <div class="about">
    <h1>This is an about {{hensu}} page</h1>
    <span v-text="count" />
         <button @click="increment">+</button>
    <button @click="decrement">-</button>

    <br>
    <span v-text="state.info" /> 
    <button @click="dbaccessed">db</button>
    <div>
      <input v-model="state.newdata" placeholder="userstable">
      <button @click="dbinsert">dbinsert</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent , ref ,reactive} from "vue";
import axios from "axios";

export default defineComponent({
  setup() {
    const count = ref(0);
    const increment = () => (count.value += 1); // thisが消えた
    const decrement = () => (count.value -= 1); // thisが消えた

    const state = reactive({
      info: "first",
      newdata:"shoki"
    });
    const dbaccessed = () => {
      axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      //.get('https://20210317ota.azurewebsites.net/api/HttpTrigger3?code=jGQgQDfPiGu59DOLkscM2AuBncpPQ9LC6PzpJ8sM0SSjzlqGtcOSRQ==')
      //.post('https://20210317ota.azurewebsites.net/api/HttpTrigger3?code=jGQgQDfPiGu59DOLkscM2AuBncpPQ9LC6PzpJ8sM0SSjzlqGtcOSRQ==',{"name":"ota"})
      //.post('https://api.coindesk.com/v1/bpi/currentprice.json',)
      .then((response) => {
        state.info = response.data;
      });
    }
    const dbinsert = () => {
      state.info = state.newdata;
      axios
      //.get('https://api.coindesk.com/v1/bpi/currentprice.json')
      //.get('https://20210317ota.azurewebsites.net/api/HttpTrigger3?code=jGQgQDfPiGu59DOLkscM2AuBncpPQ9LC6PzpJ8sM0SSjzlqGtcOSRQ==')
      .post('https://20210317ota.azurewebsites.net/api/HttpTrigger3?code=jGQgQDfPiGu59DOLkscM2AuBncpPQ9LC6PzpJ8sM0SSjzlqGtcOSRQ==',{"name":"ota"})
      //.post('https://api.coindesk.com/v1/bpi/currentprice.json',)
      .then((response) => {
        state.info = response.data;
      });

    }
    return {
      count,
      state,
      increment,
      decrement,
      dbaccessed,
      dbinsert
    };
  }});

</script>

