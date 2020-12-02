<template>
  <div id="app">
     <Header
     v-bind:color-jugar='colorJugar'
     v-bind:gano='gano'
     ></Header>
      <br>
     <Botones  v-bind:mensaje='mensaje' 
      v-bind:restart="restart"
       v-bind:dificultadEasy="dificultadEasy"
       v-bind:dificultadHard="dificultadHard"
       v-bind:is-Hard='isHard' >
    </Botones>

    <Color v-for="(color, index) in colors"
            v-bind:color="color"
            v-bind:color-clikeado='colorclickeado'
            v-bind:index="index"
            v-bind:key="myKey(color)" 
            v-bind:colors='colors'
            v-bind:conocer-ganador="conocerGanador">
    </Color>

    </div>
</template>

<script>
import Header from './components/Header.vue'
import Botones from './components/Botones.vue'
import Color from './components/Color.vue'



export default {
  name: 'App',
  data () {
    return {
      colorJugar: {
           r: 0,
           g: 0,
           b: 0
       },
       colors: [],
       mensaje:"",
       colorclickeado:"",
       isHard:true,
       colorCount:6,
       gano:false

    }
  },
   
   mounted () {   
      this.restart()   
    },

  methods: {
        conocerGanador(colorcuadrado, cuadradoIndex){
            if(JSON.stringify(colorcuadrado) === JSON.stringify(this.colorJugar)){
                this.mensaje="Ganaste!";
                this.gano=true;
                for (let index = 0; index < this.colors.length; index++) {
                    Object.assign(this.colors[index], colorcuadrado);
                  }
            }else{
                this.mensaje="Intenta de nuevo!";
                // le pongo el color del body para que parezca que desaparece
                this.colors[cuadradoIndex].r = 255;
                this.colors[cuadradoIndex].g = 255;
                this.colors[cuadradoIndex].b = 255;
            }
        },
         
        myKey(color){
            const randomNumber = Math.random() * 100000;
            return '' + randomNumber + color.r +color.g +color.b;
        },

        dificultadEasy(){
            if (this.isHard) {
                this.isHard = false;
                this.colorCount = 3;
                this.restart();
            }
        },
        dificultadHard(){
            if (!this.isHard) {
                this.isHard = true;
                this.colorCount = 6;
                this.restart();
            }
        },
        restart(){
          //  this.colors.splice(0, this.colors.length, ...this.createNewColors(this.colorCount));
            this.colors=this.createNewColors(this.colorCount);
            let pickedColor = this.colors[this.pickColor()];
            this.colorJugar.r = pickedColor.r;
            this.colorJugar.g = pickedColor.g;
            this.colorJugar.b = pickedColor.b;
            this.mensaje="";
            this.gano=false;

        },
        createNewColors(numbers){
            let arr = [];
            for (var i = 0; i < numbers; i++) {
                arr.push(this.createRandomStringColor());
            }
            return arr;
        },
        createRandomStringColor(){
            return {
                r: this.randomInt(),
                g: this.randomInt(), 
                b: this.randomInt()
            };
        }, 
        randomInt(){
            return Math.floor(Math.random() * 256);
        },
        pickColor(){
            let quantity = 3;
            if (this.isHard) {
                quantity = 6;
            }
            return Math.floor(Math.random() * quantity );
        },        

    },

  components: {
    Header,
    Botones,
    Color
  }


}
</script>

<style>

body {
  background: #FFFFFF;
}
</style>
