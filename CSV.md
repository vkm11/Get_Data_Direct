<template>
  <div>
    <vs-button>
       <vue-json-to-csv :json-data=kycreport>Export CSV</vue-json-to-csv>
    </vs-button>
  </div>
</template>

<script>
import VueJsonToCsv from 'vue-json-to-csv';
export default {
    name:"Ecport-CSV",
    components:{
        VueJsonToCsv
    },
}
</script>
