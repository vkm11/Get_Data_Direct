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



<!-- Button Center -->
 <div class="d-flex text-center">
     <vs-button class="m-3" :disabled="kycreport == ''">
         <vue-json-to-csv :json-data=kycreport>Export CSV</vue-json-to-csv>
     </vs-button>
     <vs-button class="m-3" :disabled="kycreport == ''">
         <vue-json-to-csv :json-data=kycreport>Export PDF</vue-json-to-csv>
     </vs-button>
 </div>
 <!-- Button Center-->
