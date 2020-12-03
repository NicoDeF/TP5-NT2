<template>

 <div id="container">
  <div class="square" :style="{'background-color': backgroundColor}" @click="mostrarColor"></div>
  </div>

</template>

<script>

  export default  {
    name: 'src-components-cuadrado-color',
    //props: ['color','index','conocerGanador','colorClikeado'],
   
 props: {
    index:Number,
    conocerGanador:Function,
    color: Object ,
    colorclikeado:Function
      }
      ,
    mounted () {

    },
    data () {
      return {
            backgroundColor: `rgb(${this.color.r},${this.color.g},${this.color.b})`,
            
      }
    },  
    methods: {
       mostrarColor(){
            this.conocerGanador(this.color, this.index);
        },
    },
}

</script>

<style scoped lang="css">

 .square {
  width: 25%;
  padding-bottom: 30%;
  float: left;
  margin: 2%;
  border-radius: 10%;
  transition: background 0.8s;
  -webkit-transition: background 0.8s;
  -moz-transition: background 0.8s;
}
pre {
  color: white;
}
</style>

