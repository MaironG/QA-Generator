<template>
  <div>
    <h1 class="texto">Introduce el texto</h1>
    <form class="formC">
     
      <textarea class="textA" id="nombre" type="text" v-model="QrcodeVue"></textarea>
      <button type="submit" class="btn" v-on:click='downloadLink("QR-G","http://localhost:3000/qr-generation")'>Descargar</button>
    </form>
    <br>
    <div id="div-canva"><qrcode-vue id="canva" v-if="QrcodeVue" :value="QrcodeVue" :margin="1"  :size="300" level="H" /></div>
  </div>
</template>

<script>
import QrcodeVue from 'qrcode.vue'

export default {
  name: "Qr-generation",
  data() {
      return {
        QrcodeVue:null,
        texto: "",
      }
      },
    components: {
      QrcodeVue

    },
    methods:{
    downloadLink(name, href) {
    console.log();
    var link = document.createElement('a');
    link.download = name;
    console.log(href);
    link.href = document.getElementById('canva').toDataURL()
    link.click();
      }
    },
  }

</script>
<style>
  .btn {
    background-color: #087b0c; /* Green */
  
  color: white;
  padding: 10px 15px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  }

  .texto{
    color: black;
  }
  
  .textA{
    padding: 10px 15px;
    margin-right: 10px;
  }

  .formC{
    display:inline-flex;
  }

</style>
