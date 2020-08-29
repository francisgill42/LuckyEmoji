<template>

<v-row>

<v-col>
    <v-card v-if="msg" outlined color="red" class="secondary pa-2 text-center">
    {{msg}} 
    </v-card>     
</v-col>


<v-col cols="12">
<p class="subheading white--text">Your coins : {{coins}} </p>
<hr class="my-3">
<v-btn :disabled="disabled" @click="start" class="purple white--text" >
Start
</v-btn>  
<v-btn @click="reset" class="purple white--text" >
Stop
</v-btn>    

</v-col>


<v-col class="mt-5" cols="4" v-for="(option,i) in options" :key="i">
 <v-card width="30%" style="border-radius:100%;" outlined :color="option.color" class="pa-1 text-center">
  <v-btn style="border-radius:70%;" @click="my_num(option.text)" :color="option.color" class="pa-5" >
  {{option.text}}  
  </v-btn>    
 </v-card>
</v-col>
</v-row>
</template>

<script>
//import Logo from '~/components/Logo.vue'

export default {

  data : () => ({
    disabled : false,
    num : 0,
    counter : 0,
    coins:5,
    msg : '',
    options : [
      {text:'😀',color:'white'},
      {text:'😁',color:'white'},
      {text:'😂',color:'white'},
      {text:'🤐',color:'white'},
      {text:'😍',color:'white'},
      {text:'😅',color:'white'},
      {text:'😆',color:'white'},
      {text:'😉',color:'white'},
      {text:'😎',color:'white'},
    ],
    my_Var : '',
  }),
  components: {
  // add your component name here 
  },
  methods:{
    getRandom () {
      return Math.floor(Math.random(1000-10000) * 5000)
    },

    start(){


       if(this.num == 0){
        alert('select your number before start the game');
         return false;
        }

        if(this.coins == 0){
        alert('you dont have enough coins');
        return false;
        }

        this.my_Var = setInterval(this.run,100);
        setTimeout(() => {
              this.stop()
              this.disabled = false
          },this.getRandom());
      
    },
    run () {
      this.disabled = true;
      this.getCounter()
      this.getColors()
    },
    getCounter () { 
      this.counter == 9 ?  this.counter = 1 : this.counter++ 
    },
    getColors () {
      var counter = this.counter - 1
      var i = 0
      var color = ''
      
      for(i = 0; i < 9; i++){
      
        color = this.options[i] == this.options[counter] ? 'purple' : 'white';
        this.options[i].color = color

        
      }
    },
    stop(){
      clearInterval(this.my_Var);
      this.winOrnot();

      
    },
    winOrnot () {

        if(this.num == this.options[this.counter - 1].text){
          this.coins+=5;
          alert('you won');
          alert('you earned 5 more coins. now your total coins are ' + this.coins);
          this.num = 0;
        }
        else{
         this.coins--;
          alert('you remaining coins: ' + this.coins);
        }
    },
    reset () {

    this.counter == 0 ? this.getColors : this.options[this.counter - 1].color = 'white';
    this.counter = 0;
    this.num = 0;
      
    },
    my_num(v){
      this.num = v
      alert('your emoji : ' + this.num)
    }
  }
}
</script>
