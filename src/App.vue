<template>
  <div>
    <Header :totalIncome="state.totalIncome" />    
  </div>
</template>

<script>
import {reactive, computed} from 'vue';
import Header from './components/Header.vue';
export default {
  setup() {
    const state = reactive({
      income: [],
      totalIncome: computed(() => {
        let temp = 0;
        if (state.income.length > 0) {
          for (let i = 0; i < state.income.length; i++) {
            temp += state.income[i].value;
          }
        }
        return temp;
      })
    });
    return {
      Header,
      state
    }
  },
  components: {
    Header
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;
}

body {
  background: #eee;
}
</style>
