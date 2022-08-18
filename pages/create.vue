<template>
<v-card style="background-color:ivory; border-radius: 1%; border: 2px solid #073b5b">
  <v-form>
    <v-container>
      <v-row>
        <v-col>
          <v-container style=" background-color: ivory; border-radius: 7px">
            <h1 style="text-align:center;font-family:system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif">Cadastro De Cursos</h1>
            <v-divider style="color: #073b5b"></v-divider>
            <v-container style="padding: 5%; background-color: ivory;">
              <v-row>
                <v-col>
                  <v-text-field
                    label="Nome Do Curso *"
                    v-model="universidade.name"
                    outlined
                    :rules="rule"
                    required
                    placeholder="Obrigatório"
                    color="#073b5b"
                  ></v-text-field>
                </v-col>
                <v-col>
                    <v-text-field
                    label="Código oficial Do Curso *"
                    v-model="universidade.id"
                    outlined
                    required
                    placeholder="Obrigatório"
                    :rules="rule"
                    color="#073b5b"
                  ></v-text-field>
                  </v-col>
              </v-row>
              <v-row>
                <v-col>
                    <v-text-field
                    label="Nome do Coordenador do Curso"
                    outlined
                    v-model="universidade.idCoord"
                    placeholder="Opcional"
                    color="#073b5b"
                  ></v-text-field>
                  </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <v-textarea
                    outlined
                    label="Observações"
                    color="#073b5b"
                    v-model="universidade.observacoes"
                    placeholder="Opcional"
                  ></v-textarea>
                </v-col>
              </v-row>
              <v-card-actions>
                <v-btn
                  dark
                  to="/"
                  color="red"
                  elevation="0"
                >
                  Cancelar
                </v-btn>
                <v-spacer></v-spacer>
                <v-btn
                  :disabled="!formIsValid"
                  dark
                  elevation="0"
                  color="#073b5b"
                  @click="cadastro"
                >
                  Cadastrar
                </v-btn>
              </v-card-actions>
            </v-container>
          </v-container>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</v-card>
</template>

<script>
export default {
  name: "CreateIndexPage",
  data(){
    return{
      universidade: {
        name: null,
        id:null,
        idCoord:null,
        observacoes:null
      },
      rule: [p => !!p || 'Esse campo é obrigatório!']
    }
  },
  computed: {
    formIsValid(){
      return(
        this.universidade.name &&
        this.universidade.id
      )
    }
  },
  created(){
    console.log(this.$route?.params);
    if(this.$route?.params.item){
      this.universidade = this.$route.params.item
    }
  },  
  methods:{
    cadastro (){
      this.$router.push({
        name: 'index'
      })
    }
  }
}
</script>

<style>

</style>