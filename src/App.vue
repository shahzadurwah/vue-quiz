<template>
  <div class="container">
    <div class="row  justify-content-center">
      <div class="col-sm-12 col-md-8 p-3 mt-5 text-center">
        <transition name="flip" mode="out-in">
                  <component :is="mode" @istrue="istrue" @confirmed="mode='Quiz'"></component>

        </transition>
       
      </div>
    </div>
  </div>
</template>

<script>
import Quiz from './components/Quiz.vue';
import Answer from './components/Answer.vue';
export default {
  data(){
    return{
      mode:'Quiz'
    }
  },
  methods:{
    istrue(data){
      if(data){
        this.mode='Answer'
      }else{
        this.mode='Quiz';
        alert("Wrong Answer Please Try Again!")
      }
    },
    

  },
    components: { Quiz, Answer }
}
</script>

<style>
body{
  background-color: lightgreen;
}

  .flip-enter-active{
    animation: flip-in 0.3s ease-out forwards;
  }
  .flip-leave-active{
    animation: flip-out 0.3s ease-out forwards;

  }

  @keyframes flip-in{
    from{
      transform: rotateY(90deg);
    }to{ 
      transform: rotateY(0deg);
    }

  }
  @keyframes flip-out{
    from{
      transform:rotateY(0deg)
    }to{ 
      transform: rotateY(90deg);
    }

  }
</style>