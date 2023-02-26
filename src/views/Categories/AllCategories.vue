
<template>
<v-container fluid>
    <v-row>
        <v-col cols="2"></v-col>
        <v-col cols="8">
  <v-card >
    <!-- <v-card-title>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title> -->
    <v-data-table
      :headers="headers"
      :items="allcategory"
      
    >
    
</v-data-table>
  </v-card>
</v-col>
        <v-col cols="2"></v-col>
    </v-row>

</v-container>
</template>

<script>
import { mapGetters ,mapActions} from 'vuex';
export default{
    name:"AllCategories",
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
        categories : []
        }
    },
    computed:mapGetters(["allcategory"]),
    methods:{
        ...mapActions(["getCategory"])
    },
    created(){
        this.getCategory()
        
    }

}
</script>