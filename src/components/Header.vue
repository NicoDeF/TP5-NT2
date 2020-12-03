<template>
 <div id="header" :style="{'background-color': getBackGroundFromPrincipal}">

		<h1>The Great <br>
			<span id="colorDisplay">rgb({{colorJugar.r}}, {{colorJugar.g}}, {{colorJugar.b}})</span>
			<br>
            Guessing Game
        </h1>
	</div>

</template>

<script>

  export default  {
    name: 'HeaderJuego',
    props: ['colorJugar', 'gano'],
    mounted () {

    },
    data () {
      return {
      }
    },
    methods: {

    },
    computed: {
      
      getBackGroundFromPrincipal(){
        const bkc = `rgb(${this.colorJugar.r},${this.colorJugar.g},${this.colorJugar.b})`;
        let value;
        if (this.gano) {
          value= bkc;
        } else {
          value= "rgb(34, 80, 139)";
        }
            return value;
        }
    }
}


</script>

<style scoped lang="css">
  h1 {
  font-weight: normal;
  line-height: 1.1;
  padding: 10px ;
}
#colorDisplay {
  font-size: 150%;
}
#header {
	background: rgb(70, 180, 147);
	text-transform: uppercase;
	text-align: center;
	margin: 0;
	color: white;
}
</style>
