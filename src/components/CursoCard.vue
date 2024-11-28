<template>
  <div>
  <v-row>
  
    <v-col
  v-for="(arrayEscolhido, index) in arrayEscolhido"
  :key="index"
  cols="12"
  sm="6"
  md="4"
  lg="4"
  xl="4"
>
    <v-card
      max-width="344"
      style="margin-top: 20px; margin-left: 110px," 
    >
      <v-img
        :src="arrayEscolhido.pera"
        alt="Imagem"  
        height="200px"
        style="padding-top: 400px

;"
      ></v-img>

     
    <div
    style="margin-left: 80px;">
      
     <v-card-title>{{ arrayEscolhido.name }} </v-card-title>
    </div>
      <v-card-title>{{ arrayEscolhido.subtitulo }} </v-card-title>

      <v-card-subtitle>{{arrayEscolhido.local }}</v-card-subtitle>
      <v-card-subtitle> {{arrayEscolhido.local }} </v-card-subtitle>
      
    
     
  

      <v-card-actions>
        <v-btn color="orange lighten-2" text>Explore</v-btn>

        <v-spacer></v-spacer>

        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>
            {{ arrayEscolhido.sobre }}
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </v-col>

</v-row>
  <div
  style="align-items: center;">

<v-btn 
style="background-color:#b25f83;
margin-top: 10%;
margin-left: 15%;
width: 300px;
height: 100px;
border-radius: 50px;
color: aliceblue;
font-size: 40;"
href=" https://doity.com.br/tabela-de-valores"  target="_blank">

<h1>tabela</h1>
</v-btn>
<v-btn 
style="background-color: #b25f83;
margin-top: 10%;
margin-left: 15%;
width: 300px;
height: 100px;
border-radius: 50px;
color: aliceblue;
font-size: 40;"
href="https://doity.com.br/simulacao-de-hpp"  target="_blank">

<h1>MINI-CURSOS</h1>
</v-btn>
</div>
</div>
</template>

<script>
export default {
props: {
  arrayEscolhido: Array   
},
data() {
  return {
    
    show: false
  };
}
}
</script>