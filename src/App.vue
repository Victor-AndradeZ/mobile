<template>
    <v-app>
    <main>
      
      <v-card class="overflow-hidden">
        <div style="padding-bottom: 220px;">
        <v-app-bar
          absolute
          color="#9f3949"
          
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
          style="color: aliceblue;"> I Simpósio multiprofissional em Saúde da Mulher - UNIFBV WYDEN”</v-toolbar-title>
  
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
              <v-tab @click="selecionarArray('Quinta')"
              style="color: aliceblue;" >Quinta</v-tab>
  
             <v-tab @click="selecionarArray('Sexta')"
             style="color: aliceblue;" >Sexta</v-tab>
  
              <v-tab @click="selecionarArray('Minicursos ')" 
              style="color: aliceblue;">Minicursos </v-tab>

              <v-tab @click="selecionarArray('submissão de trabalho')"
              style="color: aliceblue;" >submissão de trabalho</v-tab>

              <v-tab @click="selecionarArray('Apoio')"
              style="color: aliceblue;" >Apoio</v-tab>
  
            </v-tabs>
          </template>
        </v-app-bar>
        
        <CreateCard v-if="showSquareCreate" @fechar="fecharCard" 
        @CursoBCriado="PushArrayQuinta" @CursoTCriado="PushArraysexta" @CursoLCriado="PushArrayMinicursos "
   />
  
    <DeleteCard v-if="showSquareDelete" @fechar="fecharCard" :Quinta="Quinta" :Sexta="Sexta" :Minicursos: ="submissãodetrabalhos"/>
    <EditCard v-if="showSquareEdit"     @fechar="fecharCard" :Quinta="Quinta" :Sexta="Sexta" :Minicursos: ="submissãodetrabalhos"/>
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
        style="background-color: #9f3949;">
        
        
         

      
      
      <v-btn
        icon
        href="https://www.instagram.com/laesmfbv?igsh=ODhoMDU2cWI5ZGdo"
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
          style="background-color: #9f3949;">O Simpósio Multiprofissional em Saúde da Mulher é um evento de extrema relevância para a promoção da saúde feminina e para o avanço das práticas de cuidado. Esse tipo de simpósio reúne profissionais de diversas áreas da saúde para discutir e compartilhar conhecimentos sobre temas específicos relacionados à saúde da mulher. Sua importância é multifacetada e impacta positivamente tanto os profissionais da saúde quanto as mulheres que recebem os cuidados.

Primeiramente, a abordagem multiprofissional permite uma visão mais holística da saúde da mulher. Ao integrar especialistas em áreas como ginecologia, obstetrícia, endocrinologia, psicologia, nutrição, e fisioterapia, entre outras, o simpósio promove uma compreensão mais abrangente das necessidades e desafios enfrentados pelas mulheres em diferentes fases da vida. Essa integração ajuda a identificar e abordar questões de forma mais completa e eficaz, desde a prevenção até o tratamento.
        </v-card-text>
        
  
        
  
        <v-card-text class="white--text"
        style="background-color: #9f3949;">
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
        Quinta: [
       
          {
            name: " Túlio Alves",
            subtitulo:"Políticas Públicas para a Popula-ção Vulnuerável.",
            sobre: "Enfermeiro pela UFPE - CAV .Especialista em Saúde da Família em de Formato de Residência - IMIP e Mestre em Políticas Públicas - UFPE.",
            tempo: "10",
            valor: "650",
            delete: false,
            tipo: 'Quinta',
            pera: require("@/assets/download.png"),
           
         
            
          },
          {
            name: "Marx donelas",
            subtitulo:"Crosstraining na gestação.",
            sobre: "Bacharel Edução Física . Bacharel Fisioterapia . Pós graduado em Bases Fisiológicas do Treinamento e nutrição esportiva. Pós graduado em Psicomotricidade . Pós graduando em Fisiologia humana aplicada as Ciências da saúde . Docente dos Cursos de Fisioterapia e Educação Física da UniFBV Wyden Recife . CFSC L1. CrossFit L1.Atlétich Lab Performance L1. Kettlebell Sports.  ",
            tempo: "10",
            valor: "700",
            delete: false,
            tipo: 'Quinta',
            pera: require("@/assets/Marx donelas.jpg"),
           
          },
          {
            name: "Nádia Oliveira",
            subtitulo:"",
            sobre: "Psicóloga, especialista em Psicologia Humanista na Abordagem Centrda na Pessoa (UniFafire),mestra e doutora em Psicologia Cognitiva pela UFPE.Linha de estudos: supervisão e formação profissional de psicólogos.",
            tempo: "10",
            valor: "400",
            delete: false,
            tipo: 'Quinta',
            pera: require("@/assets/Nadia.jpg"),
            
          },
          {
            name: "Sérgio pessoa ",
            subtitulo:"Os direitos à saúde de pessoas t-rans",
            sobre: "Advogado e Professor Universitário . Conselheiro da Ordem dos Advogados do Brasil . Presidente da Comissão de Diversidade Sexual e de Gênero . Ativistas de pautas LGBT e Direitos Humanos. ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/sergio.jpg"),
          },
         
          {
            name: "TEREZA NOGUEIRA",
            subtitulo:"Violência Psicológica",
            sobre: "Delegada de Polícia da Mulher de PE . Mestranda em Perícias Forenses (Linha de Pesquisa Violência) e Especialista em Direito Público. Há 9 anos dedica-se, com afinco, ao Combate à Violência contra os mais Vulneráveis (Mulheres, Meninas, Adolescentes e Idosos). é  voluntária do Grupo Mulheres do Brasil, Núcleo Recife-PE, e apaixonada por Transformação Social e Cultura de Paz. É palestrante e propulsora de mulheres, já tendo sido distinguida com diversas premiações e homenagens.",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/TEREZA.jpg"),
          },
          {
            name: "Mozart Amorim",
            subtitulo:"Violência doméstica",
            sobre: "Explicaçao sobre a palestra",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/Mozart Amorim.jpg"),
          },
          
          
                                           
        ],
        Sexta: [
          {
            name: "Andressa Tavares",
            subtitulo:"Intervenções nutricionais e suplementação em mulheres com SOP",
            sobre: "Nutricionista pela Universidade Federal de Pernambuco (UFPE).Mestra em Nutrição pela Universidade Federal de Pernambuco (UFPE). Pós-graduanda em Nutrição Clínica Funcional e Fitoterápicos (CCE).Atuante em consultório desde 2020.",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/andressa.jpg"),
            
          },
          {
            name: "Thayna Praia",
            subtitulo:"Atuação da fisioterapia pélvica na saúde da mulher",
            sobre: "Explicaçao sobre a palestra",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/Thayna Praia novo.jpg"),
            
          },
          
       
         
          {
            name: "Renata rosal",
            subtitulo:"O Papel da Vigilância Epidemiológica na Promoção e Prevenção das ISTS",
            sobre: "Explicaçao sobre a palestra",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/renata.jpg"),
          },
          {
            name: "Joana Nunes",
            subtitulo:"Práticas integrativas na assistência ao parto",
            sobre: "Explicaçao sobre a palestra",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/fbvtitular.png"),
          },
         
          
            
          ],
        
          Minicursos:  [
          {
            name: " Mariana faustino",
            subtitulo:"Simulação de HPP",
            sobre: "Enfermeira pela UFPEm . Especialista em Enfermagem . Obstétrica pelo programa de residência da prefeitura Municipal do Recife. ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/Mariana Faustino.jpg"),
            
          },
          {
            name: "Enf. Jonas Gê ",
            subtitulo:"Primeiros socorros",
            sobre: "Bacharel em Enfermagem . Pós Graduando em MBA em Gestão e Administração Hospitalar e UTI - Unidade de Terapia Intensiva . Formado em BLS na AHA e pela UFRN . Preceptor em Enfermagem - UNIFBV Wyden . Servidor Público Estadual da UPE - Universidade de Pernambuco . Servidor Público Estadual da UPE - Universidade de Pernambuco . Atuante na Emergência do Hospital - PROCAPE . Coordenador da LAUREM - Liga de Urgência e Emergência UNIFBV.",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/Jonas.jpg"),
            
          },
          {
            name: " Ana Caroline Novaes ",
            subtitulo:"Interpretação de exames laborat-oriais",
            sobre: "Enfermeira formada pela Universidade de Pernambuco - UPE - FENSG 2002.2.Especialista em  Saúde Pública . Enfermeira especialista em hematologia e hemoterapia . Enfermeira Mestre em Saúde Materno Infantil . Enfermeira de Saúde da Família Prefeitura da cidade de Recife . Professora de pós graduações nas áreas de oncologia . hematologia e saúde pública . Preceptora de alunos da graduação e residência da Universidade de Pernambuco . Tutora da Residência multidisciplinar da Prefeitura da Cidade do Recife . Conselheira do Conselho Regional de Enfermagem de Pernambuco - COREN/PE . Coordenadora da Câmara Técnica da Atenção Básica  do COREN/ PE. ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/ana.jpg"),
            
          },
          {
            name: " Joana D’arc ",
            subtitulo:"Testagem rápida para IST’s da teoria a prática",
            sobre: "Enfermeira - UFPE . Especialista em Saúde da Família - IMIP/PE . Especialista em Saúde da Mulher - FAVENI . Mestranda em Saúde Coletiva - PPGSC/UFPE . Docente de Enfermagem - UNIFBV WYDEN. ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/joana dark.jpg"),
            
          },
          {
            name: " Patrícia Alves ",
            subtitulo:"Flebotomia",
            sobre: "Biomédica formada pela UNiFBV . Pós-graduada em Biomédica estética . Mestra em engenharia Biomédica UFPE . Técnica em Análises Clínicas .Técnica em Radiologia .Flebotomista .Atualmente Gerente  da Usf - unidade de saúde da família . Gestora da escola de Saúde Brasil. ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/patricia.jpg"),
            
          },
          
        ],
        submissaodetrabalho:[
        {
            name: " . ",
            subtitulo:"",
            sobre: " ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/fbvtitular.png"),
            
          },
          {
            name: " . ",
            subtitulo:"",
            sobre: " ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/fbvtitular.png"),
            
          },


        ],
        Apoio:[
       
        
          
          {
            name: " Manuella Alves ",
            subtitulo:"",
            sobre: " ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/manu.jpg"),
            
          },
          {
            name: "Escola de saude",
            subtitulo:"",
            sobre: " ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/escola.jpg"),
            
          },
          {
            name: " Cl saude",
            subtitulo:"",
            sobre: " ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/cl.jpg"),
            
          },
          {
            name: " COBRAS DO SUS ",
            subtitulo:"",
            sobre: " ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/cobras.jpg"),
            
          },
          {
            name: " manda o nome ae",
            subtitulo:"",
            sobre: " ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/imagem.jpg"),
            
          },
          {
            name: "Amanda Santana",
            subtitulo:"",
            sobre: " ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/amandadoce.jpg"),
            
          },
          {
            name: "Marx donelas",
            subtitulo:"",
            sobre: " ",
            tempo: "8",
            valor: "450",
            delete: false,
            tipo: 'sexta',
            pera: require("@/assets/dornelaspatrocionio.jpg"),
            
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