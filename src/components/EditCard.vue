<template>
  <div>
    

    <div v-if="showSquare" style="position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5); 
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  overflow-y: auto;">
       
      <div style="width: 95%;
  height:95%;
  background-color: white;
  border: 2px solid black;
  overflow-y: auto;
  
  
  ">
        
        
        <div style="display: flex;border-bottom: solid black 2px;padding-bottom: 1%;margin-top: 1%;">

<v-btn @click=DefaltShowSquarePai>Voltar</v-btn>

<div style="display: flex; padding-left: 20%;">

 <v-btn @click="selecionarArray('bacharelado')" style="margin-left: 5%;">Bacharelado</v-btn>

 <v-btn @click="selecionarArray('licenciatura')" style="margin-left: 15%;">Licenciatura</v-btn>

  <v-btn @click="selecionarArray('tecnologo')"  style="margin-left: 15%;"> Tecnólogo</v-btn>

   
</div>

</div>



<v-row style="max-height: 70%;">
  <v-col
    
    v-for="(item, index) in arrayLocal"
    :key="index"
    cols="12"
    sm="6"
    md="4"
    lg="4"
    xl="4"
    
  >
  <v-card
  
    class="mx-auto"
    max-width="400"
  >
    <v-img
      class="white--text align-end"
      height="200px"
      src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
    >
      <v-card-title>{{ item.name }}</v-card-title>
    </v-img>
 
    
  <p>Nome do curso:</p>
          <v-text-field
            v-model="item.name"
            solo
            v-bind:label="item.name"
            clearable
          ></v-text-field>
  <p>Sobre:</p>
          <v-text-field
            v-model="item.sobre"
            solo
            v-bind:label="item.sobre"
            clearable
          ></v-text-field>

    <p>Valor:</p>  
          <v-text-field
            v-model="item.valor"
            solo
            v-bind:label="item.valor"
            clearable
          ></v-text-field>
     <P>Periodos:</P>
    <v-text-field
            v-model="item.tempo"
            solo
            v-bind:label="item.tempo"
            clearable
          ></v-text-field>

          
    
          <v-btn @click="saveCursoEditado()" style="margin-left: 39%; background-color: green;">Save</v-btn>
   
  </v-card>
</v-col>

</v-row>



      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    licenciatura: Array,

    tecnologo: Array,

    bacharelado: Array  
  },

  data(){
      return{

        
        
        countries: ['Bacharelado','Tecnologo','licenciatura'],
        checkbox: true,
        show: false,

        showSquare:true,

        arrayLocal :[                            
      ]
      }
  },
  methods:{
    DefaltShowSquarePai() {
      this.showSquare = false;
    this.$emit('fechar');
    },
    
    selecionarArray(tipo) {
      if (tipo === 'bacharelado') {
    this.arrayLocal = this.bacharelado;
  } else if (tipo === 'licenciatura') {
    this.arrayLocal = this.licenciatura;
  } else if (tipo === 'tecnologo') {
    this.arrayLocal = this.tecnologo;
  }
    },

  }


}


</script>





