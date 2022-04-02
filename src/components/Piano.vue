<template>
  <div class="contenedor">
      <div class="nota" v-for="(nota, index) in notas" v-on:click="tocarNota(index+1)" 
      v-bind:key="index" :accesskey="index+1" >
      </div>
      <div class="semi-tonos">
          <div :class="`semi${indexSemitono+1}`" v-on:click="tocarSemitonos(indexSemitono+1)" v-for="(semitono, indexSemitono) in semiTonos" :key="indexSemitono"></div>
      </div>
  </div>
</template>
<script>
export default {
    data(){
        return {
            notas: ['do', 're', 'mi', 'fa', 'sol', 'la', 'si'],
            semiTonos: [1,2,3,4,5,6]
        }
    },
    methods:{
        tocarNota: function(index){
            const audio = new Audio();
            audio.src = 'notas_musicales/nota'+ index +'.wav';
            audio.load();
            audio.play();
            console.log('Nota: ' + index)
        },
        tocarSemitonos: function(indexSemitono){
            if(indexSemitono != 3){
                const audio = new Audio();
                audio.src = 'semitonos/semitono'+ indexSemitono +'.wav';
                audio.load();
                audio.play();
                console.log('Semitono: ' + indexSemitono)
            }
        }
    }
}
</script>
<style>
*{
    margin: 0;
    padding: 0;
}
.contenedor{
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    background-color: beige;
}

.nota{
    width: 80px;
    height: 300px;
    background-color: #fff;
    margin: 5px;
    transition: 0.2s;
    cursor: pointer;
}
.nota:active{
    background-color: rgb(235, 235, 235);
    box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.2);
}

.semi-tonos{
    height: 0px;
    display: flex;
    position: absolute;
    margin-top: -300px;
}
.semi1,.semi2,.semi3,.semi4,.semi5,.semi6,.semi7{
    width: 30px;
    height: 200px;
    background-color: #000;
    position:relative;
    margin: 0px 30px 0px 30px;
    cursor: pointer;
}
.semi1:active,.semi2:active,.semi3:active,.semi4:active,.semi5:active,.semi6:active{
    background: rgb(80, 80, 80);
    box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.2);
}

.semi3, .semi7{
    background: none;
    display: block;
    pointer-events: none;
}

@media (max-width:850px) {
    .nota{
        width: 60px;
        margin: 5px;
    }
    .semi1,.semi2,.semi3,.semi4,.semi5,.semi6,.semi7{
        width: 20px;
        margin-left: 20px;
    }
}

@media (max-width:630px){
    .contenedor{
        flex-direction: column;
    }
    .nota{
        width: 70%;
        height: 10%;
    }
    .semi-tonos{
        width: 40%;
        height: 100%;
        flex-direction: column;
        justify-content: center;
        margin-top: -5%;
        margin-right:-23% ;
    }
    .semi1,.semi2,.semi3,.semi4,.semi5,.semi6,.semi7{
        width: 100%;
        height: 8%;
        margin-top: 10%;
        margin-bottom: 4%;
     }
}

</style>