<template>

<v-row>
<!-- 
  <v-card v-if="msg" outlined color="red" class="secondary pa-2 text-center">
  {{msg}}
  </v-card>     
-->

<v-col cols="12">
<v-card  flat>
<v-card-text>        
<p class="subheading">Your score : {{score}} </p>
<hr class="my-3">
</v-card-text>
</v-card>

<v-col>
  <v-btn :disabled="disabled" @click="start" class="purple white--text" >
Start
</v-btn>  
<v-btn @click="stop" class="secondary white--text" >
Stop
</v-btn>    

</v-col>
<hr class="my-3">
<!-- road line  -->
<v-card class="line red text-center mt-2 mb-5" ></v-card>
<v-card class="line text-center mt-2 mb-5" ></v-card>
<v-card class="line text-center mt-2 mb-5" ></v-card>
<v-card class="line text-center mt-2 mb-5" ></v-card>
<v-card class="line text-center mt-2 mb-5" ></v-card>
</v-col>

<v-alert>😎</v-alert>
</v-row>
</template>

<script>
//import Logo from '~/components/Logo.vue'

export default {

  data : () => ({
    counter1 : 0,
    disabled : false,
    score:0,
    my_Var : '',
  }),
  computed: {
    test(){
      return '150px'
    }
  },

  methods:{

   
    start(){
      this.my_Var = setInterval(this.run,100);
    },
    run () {
      this.counter1++
    },
    stop(){
      clearInterval(this.my_Var);
    }



  }
}
</script>

<style scoped>
.line{
  height: 250px;
  width: 30px;
  margin: 0px auto;
  top: 10%;
}
</style>
