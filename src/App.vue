<template>
 <Table :apiData="state.data" v-show="state.loaded" />
<Loading v-if="state.loading" />
 <Error v-if="state.error"/>
</template>

<script>
import { onMounted, reactive } from 'vue'
import Table from "./components/Table.vue";
import Error from "./components/Error.vue";
import Loading from "./components/Loading.vue";
import axios from "axios"
export default {
  name: "App",
  components: {
Table,
Error,
Loading
  },

  setup() {
  const state = reactive({
  data: {},
  loading: null,
  error: false,
  loaded:false
});
     let loadData =  async ()=>{
       let url =`https://244b8df3-7491-4cfd-a48b-267f19446372.mock.pstmn.io/`
       state.loading= true,
       state.error=false,
       state.loaded=false
       try{
         let apiResponse = await axios.get(url)
        
         state.data = apiResponse?.data
         state.loaded=true

       }
       catch(e){
         state.error= true
         console.log("error occurred", e)
       }
       finally{
         state.loading= false
       }
     }
   onMounted(loadData())
    return {
      state
    };
  },
};
</script>

<style scoped>
.app {
  color: white;
  overflow: hidden;
}

</style>
