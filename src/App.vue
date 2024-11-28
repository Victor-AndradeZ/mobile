<template>
    <v-app>
    <main>
      
      <v-card class="overflow-hidden">
        <div style="padding-bottom: 220px;">
        <v-app-bar
          absolute
          color="#b25f83

"
          
          shrink-on-scroll
          prominent
          
          scroll-target="#scrolling-techniques-4"
          style="margin-bottom:100px ;"
        >
          <template v-slot:img="{ props }">
            <div class="img-container">      
            <v-img
            
             v-bind="props"
              gradient="to top right, rgba(100,16,100,.7), rgba(22,32,72,.7)"
              style="object-fit:right;object-position:right; width:100%; height: 1%;  ;transform: scale(1   );  ;" 
            ></v-img>
          </div>
          </template>
          
         
  
          
  
          <v-app-bar-nav-icon></v-app-bar-nav-icon>
  
          <v-toolbar-title
          style="color: aliceblue;">Plena mente</v-toolbar-title>
  
          <v-spacer></v-spacer>
  
          <v-btn icon>
            <v-icon
            style="color: aliceblue;">mdi-magnify</v-icon>
          </v-btn>
  
          <v-btn icon>
            
            <v-icon
            style="color: aliceblue;">mdi-heart</v-icon>
          </v-btn>
          
          <v-menu
            bottom
            Right
          >
            
  
            <v-list>
              <v-list-item>
                <button @click="AbrirCreateCard" style="border-bottom:solid black 1px;">Adicionar curso</button>
                       
              </v-list-item>
  
              <v-list-item>
                <button @click="AbrirDeleteCard" style="border-bottom:solid black 1px;">Remover curso</button>
              </v-list-item>
  
              <v-list-item>
                <button @click="AbrirEditCard" style="border-bottom:solid black 1px;" >Editar curso</button>
              </v-list-item>
  
              
            </v-list>
          </v-menu>
  
          <template v-slot:extension>
            <v-tabs align-with-title>
              
  
             <v-tab @click="selecionarArray('Sexta')"
             style="color: aliceblue;" >psicóloga</v-tab>
  
              <v-tab @click="selecionarArray('Minicursos ')" 
              style="color: aliceblue;">fonoaudióloga </v-tab>

              <v-tab @click="selecionarArray('submissão de trabalho')"
              style="color: aliceblue;" >submissão de trabalho</v-tab>

              <v-tab @click="selecionarArray('Apoio')"
              style="color: aliceblue;" >Apoio</v-tab>
  
            </v-tabs>
          </template>
        </v-app-bar>
        
        <CreateCard v-if="showSquareCreate" @fechar="fecharCard" 
        @CursoBCriado="PushArraypsicólogo" @CursoTCriado="PushArraysexta" @CursoLCriado="PushArrayMinicursos "
   />
  
    <DeleteCard v-if="showSquareDelete" @fechar="fecharCard" :psicólogo="psicólogo" :Sexta="Sexta" :Minicursos: ="submissãodetrabalhos"/>
    <EditCard v-if="showSquareEdit"     @fechar="fecharCard" :psicólogo="psicólogo" :Sexta="Sexta" :Minicursos: ="submissãodetrabalhos"/>
      </div>     
      <CursoCard :arrayEscolhido="arrayEscolhido"/>
        <v-sheet
          id="scrolling-techniques-4"
          class="overflow-y-auto"
          max-height="1000"
        >
  
        
          <v-container style="height: 400px;"></v-container>
  
          
        </v-sheet>
      </v-card>
  
      <template>
    <v-footer
      dark
      padless
    >
      <v-card
        flat
        tile
        class="indigo lighten-1 white--text text-center"
      >
        <v-card-text 
        style="background-color: #b25f83

;">
        
        
         

      
      
      <v-btn
        icon
        href="https://www.instagram.com/danisouzapsi22/"
        target="_blank"
        rel="noopener"
      >
        <v-icon>mdi-instagram</v-icon>
      </v-btn>

      
     

      <v-btn
        icon
        href="https://wa.me/qr/KWMFOF2NTOKAF1"
        target="_blank"
        rel="noopener"
     >
     <v-icon>mdi-whatsapp</v-icon>
    </v-btn>
  
           
          
        </v-card-text>
  
        
          <v-card-text class="white--text pt-0"
          style="background-color: #b25f83

;">O bem-estar físico e mental são pilares fundamentais para uma vida saudável e equilibrada. Ambos os aspectos estão profundamente interligados e influenciam diretamente a qualidade de vida de uma pessoa. Cuidar do corpo e da mente não é apenas uma questão estética ou de desempenho, mas uma necessidade para garantir uma vida plena e saudável, com capacidade para lidar com os desafios do dia a dia.  </v-card-text>
        
  
        
  
        <v-card-text class="white--text"
        style="background-color: #b25f83;">
          {{ new Date().getFullYear() }} —  <strong></strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </template>
    </main>
     </v-app>
    
  </template>
  
  <script>
  import CursoCard from './components/CursoCard.vue';
  import CreateCard from './components/CreateCard.vue';
  import DeleteCard from './components/DeleteCard.vue';
  import EditCard from './components/EditCard.vue';
  
  export default {
    components:{
      CursoCard,CreateCard,DeleteCard,EditCard
    },
    data() {
      return {
        showSquareDelete: false,
        showSquareCreate: false,
        showSquareEdit: false,
       
        Sexta: [
          {
            name: "Danielle Souza",
            subtitulo:"psicóloga e psicopedagoga",
            sobre: "psicologa pela Universidade Federal de Pernambuco (UFPE).Mestra em psicólogia pela Universidade Federal de Pernambuco (UFPE).",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'psicólogo',
            pera: require("@/assets/dani.jpeg"),
            
          },
          {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
          
       
         
          {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
         
            
          ],
        
          Minicursos:  [
          {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
          {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
          {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
         
          
        ],
        submissaodetrabalho:[
        {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
          {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
          {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
          


        ],
        Apoio:[
       
        
          
        {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
          {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
          {
            name: "..",
            subtitulo:"...",
            sobre: "curriculo",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/plena mente.jpeg"),
            
          },
          
                 
        
         
         
         



        ],
        arrayEscolhido:[
  
        ],
        icons: [
          
          'mdi-whatsapp',
          
          'mdi-instagram',
        ],
      };
    },
  
  methods: {
      selecionarArray(tipo) {
    
        if (tipo === 'Quinta') {
          this.arrayEscolhido = this.Quinta;
        } else if (tipo === 'Sexta') {
          this.arrayEscolhido = this.Sexta;
        } else if (tipo === 'Minicursos ') {
          this.arrayEscolhido = this.Minicursos ;
        }
       else if (tipo === 'submissão de trabalho') {
        this.arrayEscolhido = this.submissaodetrabalho; }
        else if (tipo === 'Apoio') {
          this.arrayEscolhido = this.Apoio; }

        },
      
      fecharCard() {
        this.showSquareCreate = false;
        this.showSquareDelete = false;
        this.showSquareEdit = false;
      },
      AbrirCreateCard() {
        this.showSquareCreate = !this.showSquareCreate;
      },
      AbrirDeleteCard() {
        this.showSquareDelete = !this.showSquareDelete;
      },
      AbrirEditCard() {
        this.showSquareEdit = !this.showSquareEdit;
      },
      PushArrayQuinta(NewCurso) {
        this.Quinta.push(NewCurso);
      },
      PushArraySexta(NewCurso) {
        this.Sexta.push(NewCurso);
      },
      PushArraysubmissãodetrabalhoso(NewCurso) {
        this.submissãodetrabalhos.push(NewCurso);
      },
    }
  };
  </script>