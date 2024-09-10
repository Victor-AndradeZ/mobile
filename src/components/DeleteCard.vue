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

   <v-btn @click="warning = true" style="margin-left: 65%; background-color: red;">delete</v-btn>
</div>

</div>

<v-dialog v-model="warning" max-width="400">
      <v-card>
        <v-card-title class="headline">Tem certeza que deseja excluir?</v-card-title>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" text @click="warning = false">Cancelar</v-btn>
          <v-btn color="blue darken-1" text @click="deleteCursos()">Confirmar</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

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

    <v-card-subtitle class="pb-0">
      R${{ item.valor }}/mes
    </v-card-subtitle>

    <v-card-text class="text--primary">
      <div>{{ item.name }}</div>

      <div> {{item.tempo}} Periodos</div>

      
    </v-card-text>
    <v-container
    class="px-0"
    fluid
    style="margin-left: 5%;"
  >
    <v-checkbox
      v-model="item.delete"
      :label="`delete:`"
    ></v-checkbox>
  </v-container>
    

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
              {{ item. sobre }}
            </v-card-text>
          </div>
        </v-expand-transition>
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
        checkbox: true,
        show: false,
        warning: false,

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
    
    selecionarArray(tipo){
  
  if (tipo === 'bacharelado') {
    this.arrayLocal = this.bacharelado;
  } else if (tipo === 'licenciatura') {
    this.arrayLocal = this.licenciatura;
  } else if (tipo === 'tecnologo') {
    this.arrayLocal = this.tecnologo;
  }
},

deleteCursos() {
    for (let i = this.arrayLocal.length - 1; i >= 0; i--) {
      if (this.arrayLocal[i].delete) {
        this.arrayLocal.splice(i, 1); 
      }
  }
  this.warning = false;
  },

  
  
}

}
</script>





