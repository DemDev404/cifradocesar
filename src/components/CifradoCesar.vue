<template>
  
  <div class="card">
    <h1>{{title}}</h1>

    <form>
      <!-- <output>10</output> -->
      <input type="range" v-model="desplazamiento" min="0" max="10" class="rango"/>
      <output>{{ desplazamiento }}</output>
      <input class="box" type="text" v-model="texto" placeholder="Codificar..."/>
      <div class="resultado">{{ textoCifrado(texto, parseInt(desplazamiento)) }}</div>
      <input class="box" type="text" v-model="textCod" placeholder="Decodificar..."/>
      <div class="resultado">{{ textoDecodificado(textCod, parseInt(desplazamiento)) }}</div>
    </form>
  </div>

</template>
<script>
export default{
  data(){
    return{
      title: 'Cifrador Cesar.',
      texto: '',
      textCod:'',
      desplazamiento: 0,
    }
  },
  methods: {
    textoCifrado(texto, desplazamiento){
      texto = texto.toLowerCase()
      let abc = 'abcdefghijklmnopqrstuvwxyz'
      let resultado = ''
      
      for(let i=0; i < texto.length; i++){
        if (texto[i] === ' ') {
          resultado += ' ';
        }else{
          let posicionOriginal = abc.indexOf(texto[i]);
          let nuevaPosicion = (posicionOriginal + desplazamiento) % 26;
          resultado += abc[nuevaPosicion];
        }
      }
        console.log(resultado)
      return resultado


    },
    textoDecodificado(textCod, desplazamiento){
      textCod = textCod.toLowerCase();
      const abc = 'abcdefghijklmnopqrstuvwxyz';
      let resultado = '';

      for (let i = 0; i < textCod.length; i++) {
        if (textCod[i] === ' ') {
          resultado += ' ';
        } else {
          let posicionOriginal = abc.indexOf(textCod[i]);
          let nuevaPosicion = (posicionOriginal - desplazamiento) % 26;
          if (nuevaPosicion < 0) {
            nuevaPosicion = 26 + nuevaPosicion;
          }
          resultado += abc[nuevaPosicion];
        }
      }

  console.log(resultado);
  return resultado;


    },
  },
};

</script>
<style scoped>
h1 {
  margin: 0;
}

.card {
  border-radius: 20px;
  box-shadow: 10px 10px 26px 5px rgba(0, 0, 0, 0.82);
  -webkit-box-shadow: 10px 10px 26px 5px rgba(0, 0, 0, 0.82);
  -moz-box-shadow: 10px 10px 26px 5px rgba(0, 0, 0, 0.82);
  display: block;
  padding: 2rem;
  /* min-width: 25vw;
  max-width: 40vw;
  min-height: 20vh;
  max-height: auto; */
  width: 25vw;
  height: auto;
}

input {
  background-color: #292b36;
  color: rgb(0, 219, 0);
  border: none;
  outline: none;
  height: 5rem;
  width: 100%;
  font-size: 1.2em;
  border-radius: 5px;
  padding: 0 5px;
}

.rango {
  margin: 0;
  width: 60%;
}

.resultado {
  border-radius: 10px;
  color: #ffffff;
  width: 100%;
  height: 3rem;
  margin: 1rem 0;
  padding: 5px;
  text-align: right;
  background-color: #000000;
  box-shadow: 10px 10px 26px 5px rgba(0, 0, 0, 0.82);
  -webkit-box-shadow: 10px 10px 26px 5px rgba(0, 0, 0, 0.82);
  -moz-box-shadow: 10px 10px 26px 5px rgba(0, 0, 0, 0.82);
  overflow-x: scroll;
}
::-webkit-scrollbar{
  background-color: rgba(255, 0, 0, 0);
}


</style>

