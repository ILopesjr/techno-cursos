<template>
  <div>
    <div v-if="loading">
      <PageLoading />
    </div>

    <transition>
      <div v-if="api" class="conteudo">
        <div>
          <h1>Sobre a {{ api.titulo }}</h1>
          <p>{{ api.descricao }}</p>

          <router-link class="btn-cursos" tag="button" to="/cursos"
            >Cursos</router-link
          >

          <div>
            <h2>Avaliações</h2>
            <ul>
              <li v-for="avaliacao in api.avaliacoes" :key="avaliacao.nome">
                <b>{{ avaliacao.nome }}</b>
                <p>{{ avaliacao.descricao }}</p>
              </li>
            </ul>
          </div>
        </div>

        <img src="@/assets/aprender.png" alt="Aprenda Web Design" />
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from '@/mixins/fetchData';

export default {
  name: 'HomeView',
  mixins: [fetchData],
  created() {
    this.fetchData('/home');
  },
};
</script>

<style scoped>
.btn-cursos {
  border: none;
  background-color: #4b8;
  color: #fff;
  border-radius: 4px;
  cursor: pointer;
  padding: 15px 40px;
  font-size: 1rem;
  margin-top: 10px;
  margin-bottom: 40px;
  box-shadow: 0 4px 2px rgba(0, 0, 0, 0.1);
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}
</style>
