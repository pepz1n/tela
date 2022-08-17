<template>
  <v-container>
    <v-row style="margin-top: 2%">
      <v-col>
        <template>
          <v-card>
            <v-card-title>
              Cursos Cadastrados
              <v-spacer></v-spacer>
              <v-text-field
                v-model="search"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="headers"
              :items="data"
              :search="search"
              :footer-props="{
                'items-per-page-text': 'Itens por página'
              }"
            ></v-data-table>
          </v-card>
        </template>
      </v-col>
    </v-row>  
  </v-container>
</template>

<script>
export default {
  name:'create',
  data (){
    return{
      search: '',
        headers: [
          {
            text: 'Dessert (100g serving)',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Código do Curso', value: 'id' },
          { text: 'Nome do Curso', value: 'name' },
          { text: 'Nome do Coordenador', value: 'idCoord' },
        ],
      data: [
        {name: "Ciência da computação", id: 2, idCoord:'Forg'}
      ]
    }
  }
}
</script>

<style>

</style>