<template>
    <vx-card>
        <h4 class="mb-4">KYC Reports</h4>
        <div>
            <!-- <vs-button>
                <vue-json-to-csv :json-data=jsondata>Export CSV</vue-json-to-csv>
            </vs-button> -->
        </div>

        <div class="mb-4">
            <vs-table stripe search :data="kycreport">
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

export default {
    name:"KYC-Report",
    components:{
    },
    data(){
        return{
            kycreport: [],
        }
    },
    methods:{
        loadData() {
            axios.post('http://localhost:8000/api/admin/agent/kycreport')
            .then((res) => {
                this.kycreport = JSON.parse(JSON.stringify(res.data.result.data));
                //  this.kycreport = res.data.result.data;
                console.log(this.kycreport)
            });
        }
    },
    mounted() {
        this.loadData();
    },
}
</script>
