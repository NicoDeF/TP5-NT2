<template >

 <div id="navigator">
            <button id="reset" @click="restart">New Colors</button>
            <span id="message"> {{mensaje}} </span>
            <button id="easy" v-bind:class="{ selected: !isHard }" @click="dificultadEasy">easy</button>
            <button id="hard" v-bind:class="{ selected: isHard }" @click="dificultadHard">hard</button>
    
        </div>

</template>

<script>

  export default  {
    name: 'src-components-botones',
    props: {
    restart:Function,
    dificultadEasy:Function,
    dificultadHard:Function,
    mensaje: String ,
    isHard: Boolean
      }
      ,
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {


    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  #navigator {
  background: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;
}
button {
  border: none;
  background-color: white;
  font-family: "Montserrat", "Avenir";
  text-transform: uppercase;
  height: 100%;
  font-weight: 700;
  letter-spacing: 1px;
  color: steelblue;
  transition: all 0.3s;
  outline: none;
}
button:hover {
  color: white;
  background-color: steelblue;
}
#message {
  color: black;
  display: inline-block;
  width: 20%;
}
</style>



