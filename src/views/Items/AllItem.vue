<template>
    <v-content >
        <div v-for="data in allitem" :key="data.id">{{ data }} All</div>
         </v-content>
</template>
<script>
import { mapGetters ,mapActions} from 'vuex';
export default{
    name:"AllItem",
    data(){
        return{
            headers: [
          {
            text: 'Id',
            align: 'start',
            sortable: true,
            value: 'id',
          },
          { text: 'Title', value: 'categoryname' },
          { text: 'Description', value: 'categorydes' },
          { text: 'Status', value: 'status' },
          { text: 'Action' },
     
        ],
        items : []
        }
    },
    computed:mapGetters(["allitem"]),
    methods:{
        ...mapActions(["getItem"])
    },
    created(){
        this.getItem()
        
    }

}
</script>