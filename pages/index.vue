<template>
  <v-container>
    <v-row style="margin-top: 2%">
      <v-col>
        <template>
          <v-card
            style="background-color:ivory; border-radius: 10px; border: 2px solid #073b5b"
          >
            <v-card-title style="font-family:system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif">
                <strong>
                  Cursos Cadastrados
                </strong>
              <v-spacer></v-spacer>
              <v-text-field
                v-model="search"
                append-icon="mdi-magnify"
                label="Pesquisar"
                color="#073b5b"
                single-line
                hide-details
              ></v-text-field>
              <v-spacer></v-spacer>
              <v-btn
                class="mx-2"
                fab
                elevation="1"
                small
                color="#073b5b"
                to="/create"
              >
                <v-icon
                  color="white"
                >
                  mdi-plus
                </v-icon>
              </v-btn>
            </v-card-title>
            <v-data-table
              style="background-color:ivory"
              :headers="headers"
              :items="data"
              :page.sync="page"
              :search="search"
              :items-per-page="itemsPerPage"
              color="#073b5b"
              :footer-props="{
                'items-per-page-text': 'Itens por página',
                
              }"
              hide-default-footer
              @page-count="pageCount = $event"
            >
              <template v-slot:item.actions="{ item }">
                <v-icon
                  small
                  class="mr-2"
                  @click="editar(item)"
                >
                  mdi-pencil
                </v-icon>
                <v-icon
                  small
                  @click="deletar(item)"
                >
                  mdi-delete
                </v-icon>
              </template>
            </v-data-table>
            <v-divider></v-divider>
            <v-card-actions>
              <div style="width: 10px;">
                <v-autocomplete
                  v-model="itemsPerPage"
                  label="Itens Por Página"
                  color="#073b5b"
                  style="width:1%;min-width: 1%;"
                  :items="autocomplete"
                  item-text="name"
                  item-value="name"
                ></v-autocomplete>
              </div>
            <v-spacer></v-spacer>
              <v-pagination
                v-model="page"
                :length="pageCount"
                
                circle
                color="#073b5b"
                :total-visible="5"
              >
              </v-pagination>
            </v-card-actions>
          </v-card>
        </template>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "create",
  data() {
    return {
      search: "",
      headers: [
        { text: "Código do Curso", value: "id", align: 'center' },
        { text: "Nome do Curso", value: "name", align: 'center' },
        { text: "Nome do Coordenador", value: "idCoord", align: 'center' },
        {text: "", value: "actions"}
      ],
      data: [{ name: "Ciência da computação", id: 0, idCoord: "Forg" },{ name: "Ciência da computação", id: 1, idCoord: "Forg" },{ name: "Ciência da computação", id: 2, idCoord: "Forg" },{ name: "Ciência da computação", id: 2, idCoord: "Forg" },{ name: "Ciência da computação", id: 2, idCoord: "Forg" },{ name: "Ciência da computação", id: 2, idCoord: "Forg" },{ name: "Ciência da computação", id: 2, idCoord: "Forg" },{ name: "Ciência da computação", id: 2, idCoord: "Forg" },{ name: "Ciência da computação", id: 2, idCoord: "Forg" },{ name: "Ciência da computação", id: 2, idCoord: "Forg" },{ name: "Ciência da computação", id: 2, idCoord: "Forg" }],
      autocomplete: [{name: 5}, {name: 10}, {name: 15}, {name: 20}, {name:25}, {name:30}],
      page:1,
      pageCount: 10,
      itemsPerPage:5,
    };
  },

  methods:{
    editar (item){
      console.log(item);
      this.$router.push({
        name: 'create',
        params: {item}
      })
    }
  }
};
</script>

<style>
</style>