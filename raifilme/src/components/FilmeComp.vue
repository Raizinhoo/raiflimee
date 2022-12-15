<script>
import axios from "axios";
import FilmeApi from "../api/filmes.js";
const filmeapi = new FilmeApi();
export default {
  data() {
    return {
      filme: "",
    };
  },
  components: {},
  props: {
    NomeFilme: String,
    FilmeID: Number,
    SinopseFilme: String,
  },
  async created() {
    this.filmes = await filmeapi.BuscarTodosOsFilmes();
    const url = `https://api.themoviedb.org/3/movie/${this.id}?api_key=c6de54ea3f8863d4b9fb5f5d0855dce0&language=pt-BR`;
    const { data } = await axios.get(url);
    this.filme = data;
  },
};
</script>
<template>
  <main>
    <div class="InformacoesFilme">
      <div>
        <h2 class="NomeFilme">{{ NomeFilme }}</h2>
        <p>{{ SinopseFilme }}</p>
      </div>
    </div>
  </main>
</template>
