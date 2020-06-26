<template>
  <div id="app">
    <Header :numCorrect="numCorrect" :total="total"></Header>
    <b-container class="bv-example-row">
      <b-row>
        
        <b-col sm="6" offset = "3"><QuestionBox :currentQuestion="questions[index]" v-if="questions[index]" :next="next" :increment="increment"></QuestionBox></b-col>
      </b-row>
    </b-container>
    
  </div>
</template>

<script>
import Header from './components/Header.vue'
import QuestionBox from './components/QuestionBox.vue'
export default {
  name: 'App',
  components: {
    Header,
    QuestionBox
  },
  data(){
    return{
      questions :[],
      index : 0,
      numCorrect :0,
      total:0
    }
  },
  methods:{
    next(){
      this.index ++;
    },
    increment(isCorrect){
      if (isCorrect){
        this.numCorrect ++
      }
      this.total ++
    }
  },
  mounted: function(){
    fetch('https://opentdb.com/api.php?amount=10',{
      method:'get'
      }).then((Response) => {
        return Response.json()
      }).then((jsonData)=>{
          this.questions =jsonData.results
      })
}
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
