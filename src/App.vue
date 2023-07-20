<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Item from './components/Item.vue'
import Footer from './components/Footer.vue'
</script>

<script>
// import Dados from './Dados/Services.json';

export default {
  data(){
    return{
      servicos: null
    }
  },

  //https://raw.githubusercontent.com/adilsonsilva18/link_servicos/main/src/Dados/Services.json
  //https://raw.githubusercontent.com/yurimarcon/link-services/main/src/Dados/Services.json

  mounted(){
    let target = "https://raw.githubusercontent.com/adilsonsilva18/link_servicos/main/src/Dados/Services.json";
    fetch(target)
      .then(res => res.json())
      .then(res => this.servicos = res)
      .catch(e => console.log(e))
  }
}
</script>

<template>
  <img alt="Profile" style="width:150px; border-radius:50%" 
  src="https://avatars.githubusercontent.com/u/42476449?v=4" />
  
  <h1>Adilson</h1>
  
  <blockquote cite="">
    <p>
      "O sucesso nasce do querer, da determinação e persistência em se chegar a um objetivo. Mesmo não atingindo o alvo, quem busca e vence obstáculos, no mínimo fará coisas admiráveis."
      <small> - José de Alencar - </small>
    </p>
  </blockquote>
  
  <hr/>
  <div class="items">
    <Item 
    v-for="servico, index in servicos"
    :key="index"
    :item="servico"
    />

  </div>

  <Footer />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin-bottom: 100px;
}
html{
  background: url("https://cdn.pixabay.com/photo/2023/06/21/14/17/mountain-8079469_1280.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  min-height: 100%;
}
.items{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
