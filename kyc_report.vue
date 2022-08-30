<template>
    <vx-card>
        <h4 class="mb-4">KYC Non Approval Reports</h4>
        <div>
            <vs-button class="m-3" style="float:right" :disabled="kycreport == ''">
                <vue-json-to-csv :json-data=kycreport>Export CSV</vue-json-to-csv>
            </vs-button>
            <!-- <vs-button class="m-3" style="float:right" :disabled="kycreport == ''">
                <vue-json-to-csv :json-data=kycreport>Export PDF</vue-json-to-csv>
            </vs-button> -->
            
        </div>

        <div class="mb-4" ref="content">
            <vs-table stripe search :data="kycreport" :max-items="this.kycData.per_page" pagination>
                <template slot="thead"> 
                    <vs-th>No</vs-th> 
                    <vs-th>Agency Name</vs-th> 
                    <vs-th>Agency Email</vs-th>  
                    <vs-th>Agents Name</vs-th>  
                    <vs-th>Agents Email</vs-th>  
                    <vs-th>Country</vs-th>  
                    <vs-th>Phone Number</vs-th>  
                    <vs-th>Business Type</vs-th>  
                    <vs-th>Business Category</vs-th>  
                </template> 
                <template slot-scope="{data}"> 
                    <vs-tr :key="index" v-for="(tr, index) in data">
                        <vs-td>{{ index+1 }}</vs-td>
                        <vs-td>{{ tr.agency_name }}</vs-td>
                        <vs-td>{{ tr.agency_email}}</vs-td>
                        <vs-td>{{ tr.agent_name}}</vs-td>
                        <vs-td>{{ tr.agent_email}}</vs-td>
                        <vs-td>{{ tr.country}}</vs-td>
                        <vs-td>{{ tr.agency_phone}}</vs-td>
                        <vs-td>-</vs-td>
                        <vs-td>{{ tr.business_category}}</vs-td>
                    </vs-tr> 
                </template> 
            </vs-table> 
        </div>
    </vx-card>
</template>

<script>
import axios from 'axios'; 
import VueJsonToCsv from 'vue-json-to-csv';

export default {
    name:"KYC-Report",
    components:{
        VueJsonToCsv
    },
    data(){
        return{
            kycreport: [],
            kycData: [],
        }
    },
    methods:{
        loadData() {
            axios.post('/agent/kycreport')
            .then((res) => {
                this.kycreport = JSON.parse(JSON.stringify(res.data.result.data));
                this.kycData = JSON.parse(JSON.stringify(res.data.result));
            });
        },
    },
    mounted() {
        this.loadData();
    },
}
</script>
