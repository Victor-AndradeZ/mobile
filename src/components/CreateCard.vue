<template>
  <div >
    

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
  ">
      
      <div style="width: 85%;
  height: 85%;
  background-color: white;
  border: 2px solid black;
  border-radius: 10px;
  ">
        <v-btn @click=DefaltShowSquarePai>Voltar</v-btn>
        <template>
<v-card flat>
  <v-snackbar
    v-model="snackbar"
    absolute
    top
    right
    color="success"
  >
    <span>Registration successful!</span>
    <v-icon dark>
      mdi-checkbox-marked-circle
    </v-icon>
  </v-snackbar>
  <v-form
    ref="form"
    @submit.prevent="submit"
  >
    <v-container fluid>
      <v-row>
        <v-col
          cols="12"
          sm="6"
        >
          <v-text-field
            v-model="form.first"
            :rules="rules.name"
            color="purple darken-2"
            label="Nome do curso"
            required
          ></v-text-field>
        </v-col>
        <v-col
          cols="12"
          sm="6"
        >
          <v-text-field
            v-model="form.last"
            :rules="rules.name"
            color="blue darken-2"
            label="período"
            required
          ></v-text-field>
        </v-col>
        <v-col cols="12">
          <v-textarea
            v-model="form.bio"
            color="teal"
          >
            <template v-slot:label>
              <div>
                Sobre 
              </div>
            </template>
          </v-textarea>
        </v-col>
        <v-col
          cols="12"
          sm="6"
        >
          <v-select
            v-model="form.favoriteAnimal"
            :items="animals"
            :rules="rules.animal"
            color="pink"
            label="Tipo do curso"
            required
          ></v-select>

          
        </v-col>
        <v-col
          cols="12"
          sm="6"
        >
          <v-slider
          
            v-model="form.age"
            :rules="rules.age"
            color="orange"
            label="Valor"
            hint="Be honest"
            min="1"
            max="1000"
            thumb-label
          ></v-slider>
        </v-col>
        <v-col cols="12">
          
            
          
        </v-col>
      </v-row>
    </v-container>
    <v-card-actions>
      <v-btn style=" .oi :hover{
background-color: rgba(255, 0, 0, 0.1); 
}"
        text
        @click="resetForm"
        class="oi"
        
      >
        Cancel
      </v-btn>
      <v-spacer></v-spacer>
      <v-btn
        @click='submit'
        :disabled="!formIsValid"
        text
        color="primary"
        type="submit"
        
      >
        Register
      </v-btn>
    </v-card-actions>
  </v-form>
  <v-dialog
    v-model="terms"
    width="70%"
  >
    <v-card>
      <v-card-title class="text-h6">
        Terms
      </v-card-title>
      <v-card-text
        v-for="n in 5"
        :key="n"
      >
        {{ content }}
      </v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn
          text
          color="purple"
          @click="terms = false"
        >
          Ok
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
  <v-dialog
    v-model="conditions"
    width="70%"
  >
    <v-card>
      <v-card-title class="text-h6">
        Conditions
      </v-card-title>
      <v-card-text
        v-for="n in 5"
        :key="n"
      >
        {{ content }}
      </v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn
          text
          color="purple"
          @click="conditions = false"
        >
          Ok
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</v-card>
</template>
        
      </div>
    </div>
  </div>
</template>

<script>




export default {
         
  data(){  
    
    

  const defaultForm = {
    first: '',
    last: '',
    bio: '',
    favoriteAnimal: '',
    age: null,
    terms: false
  };
    
     
    
      return{
        curso: [
      {
       nome:"",
       sobre:"",
       tempo:"",
       valor:"",
       delete: false,
       tipo :''
       
      },

    ],
        
        Tipo :'',
        showSquare: true,
        form: Object.assign({}, defaultForm),
      rules: {
        age: [
          val => val < 10 || `I don't believe you!`,
        ],
        animal: [val => (val || '').length > 0 || 'This field is required'],
        name: [val => (val || '').length > 0 || 'This field is required'],
      },
      animals: ['Bacharelado', 'Licenciatura', 'Tecnologo'],
      conditions: false,
      content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet. Duis sagittis ipsum. Praesent mauris. Fusce nec tellus sed augue semper porta. Mauris massa. Vestibulum lacinia arcu eget nulla. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Curabitur sodales ligula in libero. Sed dignissim lacinia nunc.',
      snackbar: false,
      terms: false,
      defaultForm,
      }
  },

  computed: {
    formIsValid () {
      return (
        this.form.first &&
        this.form.last &&
        this.form.favoriteAnimal 
        
      )
    },
  },
  
  methods:{
    DefaltShowSquarePai() {
      this.showSquare = false;
    this.$emit('fechar');
    },
    resetForm () {
      this.form = Object.assign({}, this.defaultForm)
      this.$refs.form.reset()
    },
    submit () {
      this.snackbar = true
      this.curso.tipo
      this.curso.name = this.form.first;
      this.curso.sobre = this.form.bio;
      this.curso.tempo = this.form.last;
      this.curso.valor = this.form.age;
      this.Tipo = this.form.favoriteAnimal;
      

      if (this.Tipo === 'Bacharelado') {
        this.$emit("CursoBCriado", this.curso);
    } else if (this.Tipo === 'Licenciatura') {
      this.$emit("CursoLCriado", this.curso);
    } else if (this.Tipo === 'Tecnologo') {
      this.$emit("CursoTCriado", this.curso);
    } else 
    this.showSquare = false;


      this.resetForm()
    },
      
      
   
  }


  
 

}
</script>