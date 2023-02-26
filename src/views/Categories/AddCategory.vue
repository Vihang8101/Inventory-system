<template>
  <v-container fluid>
    <v-row>
      <v-col cols="2"></v-col>
      <v-col cols="8">
        <v-form ref="form" @submit.prevent="onSubmit" v-model="valid" lazy-validation>
          <v-text-field
            v-model.lazy="category.categoryname"
            :counter="10"
            :rules="nameRules"
            label="Name"
            required
          ></v-text-field>

          <v-textarea
            v-model.lazy="category.categorydes"
            :counter="50"
            :rules="DescriptionRules"
            label="Description"
            required
          ></v-textarea>

          <v-radio-group v-model.lazy="category.status" row >
            <v-radio label="Active" value="Active"></v-radio>
            <v-radio label="InActive" value="InActive"></v-radio>
          </v-radio-group>

          <v-btn
            :disabled="!valid"
            color="success"
            class="mr-4"
            type="submit"
          >
            AddCategory
          </v-btn>

        </v-form></v-col
      >
     
    </v-row>
  </v-container>
</template>
      <script>
      import { mapActions } from 'vuex';
export default {
  data: () => ({
    valid: true,
    category: {
      categoryname: "",
      categorydes: "",
      status: "",
    },
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
    ],

    DescriptionRules: [
      (v) => !!v || "Description is required",
      (v) => (v && v.length <= 50) || "Description must be valid",
    ],
    
  }),

  methods: {
    ...mapActions(["setitem"]),
    onSubmit() {
        console.log("hello",this.category)
      this.$refs.form.validate();
      this.setCategory({
        categoryname:this.category.categoryname,
        categorydes:this.category.categorydes,
        status : this.category.status
      })
     
      this.category.categoryname = "",
      this.category.categorydes ="",
      this.category.status =""
      this.$refs.form.reset();
      alert("added")  
    },
    
    
  },
};
</script>