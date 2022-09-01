<template>
  <div class="card shadow">
    <div class="card-body">
      <h2 class="text-center pb-3" style="text-transform: uppercase;">question & answer</h2>
      <div class="card-title bg-dark p-3 text-white">
       
        <h5 class="text-center">{{question}}</h5>
      </div>
      <div class="card-text shadow pt-3 pb-5">
        <div class="row mt-3">
            <div class="col-6">
                <button class="btn btn-primary" @click="onAnswer(this.btnData[0].correct)">{{this.btnData[0].answer}}</button>
            </div>
            <div class="col-6">
                <button class="btn btn-primary" @click="onAnswer(this.btnData[1].correct)">{{this.btnData[1].answer}}</button>
            </div>
            <div class="col-6 mt-4">
                <button class="btn btn-primary" @click="onAnswer(this.btnData[2].correct)">{{this.btnData[2].answer}}</button>
            </div>
            <div class="col-6 mt-4">
                <button class="btn btn-primary" @click="onAnswer(this.btnData[3].correct)">{{this.btnData[3].answer}}</button>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const modeAddition=1;
const modeSubtraction=2;
export default {
      data(){
    return{
        question:"Oops an Error Ocured!",
        btnData:[
          {correct:false,answer:0},
          {correct:false,answer:0},
          {correct:false,answer:0},
          {correct:false,answer:0},
        ]
    }
  },
  methods:{
      questiongenerate(){
          let firstNumber=this.generateRandnumber(1,100);
          let secondNumber=this.generateRandnumber(1,100);
          let mode=this.generateRandnumber(1,2);
          console.log(mode);
          let corectAnswer=0;
          switch(mode){
            case modeAddition:
                corectAnswer=firstNumber+secondNumber;
                this.question=`What's ${firstNumber} + ${secondNumber}?`;
                break;
            case modeSubtraction:
                corectAnswer=firstNumber-secondNumber;
                this.question=`What's ${firstNumber}- ${secondNumber}?`;
                break;
            default:
                corectAnswer=0;
                this.question='Ops an error Ocured'
                break;
          }
          this.btnData[0].answer=this.generateRandnumber(corectAnswer-10,corectAnswer+10,corectAnswer);
          this.btnData[0].correct=false;
          this.btnData[1].answer=this.generateRandnumber(corectAnswer-10,corectAnswer+10,corectAnswer);
          this.btnData[1].correct=false;
          this.btnData[2].answer=this.generateRandnumber(corectAnswer-10,corectAnswer+10,corectAnswer);
          this.btnData[2].correct=false;
          this.btnData[3].answer=this.generateRandnumber(corectAnswer-10,corectAnswer+10,corectAnswer);
          this.btnData[3].correct=false;

          let correctBtn=this.generateRandnumber(0,3);
          this.btnData[correctBtn].answer=corectAnswer;
          this.btnData[correctBtn].correct=true;
          
      },
      generateRandnumber(min,max,except){
          let rndNumber=Math.round(Math.random()*(max-min))+min;
           if(rndNumber==except){
                return this.generateRandnumber(min,max,except);
            }
          return rndNumber;
       
      },
      onAnswer(istrue){
          this.$emit('istrue',istrue);
      }
  },
  created(){
      this.questiongenerate();
  }
};
</script>

<style>
</style>