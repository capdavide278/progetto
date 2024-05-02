<template>
    <v-form v-model="valid" @submit.prevent="creaPost">
      <v-container>
        <v-row>
          <v-col
            cols="12"
            md="4"
          >
            <v-text-field
              v-model="formData.userId"
              :counter="10"
              :rules="nameRules"
              label="Titolo"
              hide-details
              required
            ></v-text-field>
          </v-col>
  
          <v-col
            cols="12"
            md="4"
          >
            <v-text-field
              v-model="formData.voto"
              :counter="10"
              :rules="nameRules"
              label="Voto Personale"
              hide-details
              required
            ></v-text-field>
          </v-col>
  
          <v-col
            cols="12"
            md="4"
          >
            <v-text-field
              v-model="formData.body"
              :rules="emailRules"
              label="Impressione film"
              hide-details
              required
            ></v-text-field>
          </v-col>
        </v-row>
        <v-btn
        :loading="loading"
        class="mt-2"
        text="Invia"
        type="submit"
        block
      ></v-btn>
      </v-container>
    </v-form>
  </template>
<script>
import axios from 'axios'
    export default{
        name: 'createPost',
        data(){
            return{
                formData:{
                    userId:'',
                    voto:'',
                    body:''
                }
            }
        },
        methods:{
            creaPost(){
                axios.post('https://jsonplaceholder.typicode.com/posts', this.formData)
                .then(response => console.log(response))
                .catch(error => console.log(error))
            }
        }
    }
</script>

<style scoped>

</style>