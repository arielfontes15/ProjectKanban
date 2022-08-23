<template>
    <div>
      <HeaderKanban />
      <div class="board">
        <div class="lane">
          <h2 class="lane-title">Backlog</h2>
          <CardKanban
            v-for="card in dataCard.backlog"
            :key="card.id"
          >
            {{card.text}}
          </CardKanban>
        </div>
        <div class="lane">
          <h2 class="lane-title">Desenvolvimento</h2>
          <CardKanban
            v-for="card in dataCard.dev"
            :key="card.id"
          >
            {{card.text}}
          </CardKanban>
        </div>
        <div class="lane">
          <h2 class="lane-title">Teste</h2>
          <CardKanban
            v-for="card in dataCard.teste"
            :key="card.id"
          >
            {{card.text}}
          </CardKanban>
        </div>
        <div class="lane">
          <h2 class="lane-title">Pronto</h2>
          <CardKanban
            v-for="card in dataCard.pronto"
            :key="card.id"
          >
            {{card.text}}
          </CardKanban>
        </div>
      </div>
    </div>
</template>

<script>
import HeaderKanban from './components/HeaderKanban.vue'
import CardKanban from './components/CardKanban.vue'
import initialCards from './initialCards.js'

export default {
  name: 'App',
  data(){
    return {
      dataCard: {
        backlog: initialCards.backlog,
        dev: initialCards.dev,
        teste: initialCards.teste,
        pronto: initialCards.pronto
      }
    }
  },
  components: {
    HeaderKanban,
    CardKanban,
  }
}
</script>

<style>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html{
  font-size: 62.5%;
}
body{
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #66bb6a;
}

.board{
  display: flex;
  justify-content: flex start;
  margin: 1.2rem 0.8rem;
}

.lane{
  background: #e0e0e0;
  width: 23rem;
  height: 30rem;
  border-radius: 0.8rem;
  box-shadow: 0 .1rem .2rem 0 rgba(33, 33, 33, .1);
  margin: 0 0.8rem;
  padding: 0 0.7rem;
}

.lane-title{
  padding: 0.8rem 0.5rem;
  margin-bottom: 0.6rem;
}
</style>
