<template>
    <div>
      <HeaderKanban />
      <div class="board">
        <div class="lane">
          <h2 class="lane-title">Backlog</h2>
          <Container
            group-name="kanban"
            @drag-start="handleDragStart('backlog', $event)"
            @drop="handleDrop('backlog', $event)"
            :get-child-payload="getChildPayload"
            :drop-placeholder="{className: 'placeholder'}"
          >          
            <Draggable
              v-for="card in dataCard.backlog"
              :key="card.id"
            >
              <CardKanban>
                {{card.text}}
              </CardKanban>
            </Draggable>
          </Container>
        </div>
        <div class="lane">
          <h2 class="lane-title">Desenvolvimento</h2>
          <Container
            group-name="kanban"
            @drag-start="handleDragStart('dev', $event)"
            @drop="handleDrop('dev', $event)"
            :get-child-payload="getChildPayload"
            :drop-placeholder="{className: 'placeholder'}"
          >          
            <Draggable
              v-for="card in dataCard.dev"
              :key="card.id"
            >
              <CardKanban>
                {{card.text}}
              </CardKanban>
            </Draggable>
          </Container>
        </div>
        <div class="lane">
          <h2 class="lane-title">Teste</h2>
          <Container
            group-name="kanban"
            @drag-start="handleDragStart('teste', $event)"
            @drop="handleDrop('teste', $event)"
            :get-child-payload="getChildPayload"
            :drop-placeholder="{className: 'placeholder'}"
          >          
            <Draggable
              v-for="card in dataCard.teste"
              :key="card.id"
            >
              <CardKanban>
                {{card.text}}
              </CardKanban>
            </Draggable>
          </Container>
        </div>
        <div class="lane">
          <h2 class="lane-title">Pronto</h2>
          <Container
            group-name="kanban"
            @drag-start="handleDragStart('pronto', $event)"
            @drop="handleDrop('pronto', $event)"
            :get-child-payload="getChildPayload"
            :drop-placeholder="{className: 'placeholder'}"
          >          
            <Draggable
              v-for="card in dataCard.pronto"
              :key="card.id"
            >
              <CardKanban>
                {{card.text}}
              </CardKanban>
            </Draggable>
          </Container>
        </div>
      </div>
    </div>
</template>

<script>
import HeaderKanban from './components/HeaderKanban.vue'
import CardKanban from './components/CardKanban.vue'
import initialCards from './initialCards.js'
import { Container, Draggable } from 'vue-smooth-dnd'

export default {
  name: 'App',
  components: {
    HeaderKanban,
    CardKanban,
    Container,
    Draggable
  },
  data(){
    return {
      dataCard: {
        backlog: initialCards.backlog,
        dev: initialCards.dev,
        teste: initialCards.teste,
        pronto: initialCards.pronto
      },
      draggingCard: {
        lane: '',
        index: -1,
        cardData: {},
      }
    }
  },
  methods: {
    handleDragStart(lane ,dragResult){
      const { payload, isSource } = dragResult
      if(isSource) {
        this.draggingCard = {
          index: payload.index,
          lane,
          cardData: { 
            ...this.dataCard[lane][payload.index]
          }
        }
      }
      console.log(payload)
    },
    handleDrop(lane , dropResult){
      const { removedIndex, addedIndex } = dropResult
      if(lane === this.draggingCard.lane && removedIndex === addedIndex){
        return
      }
      if(removedIndex !== null){
        this.dataCard[lane].splice(removedIndex, 1)
      }
      if(addedIndex !== null){
        this.dataCard[lane].splice(addedIndex, 0, this.draggingCard.cardData)
      }
    },
    getChildPayload(index){
      return {
        index,
      }
    }
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
  align-items: flex-start;
}

.lane{
  background: #e0e0e0;
  width: 23rem;
  border-radius: 0.8rem;
  box-shadow: 0 .1rem .2rem 0 rgba(33, 33, 33, .1);
  margin: 0 0.8rem;
  padding: 0 0.7rem;
}

.lane-title{
  padding: 0.8rem 0.5rem;
  margin-bottom: 0.6rem;
}

.placeholder {
  background: rgba(33, 33, 33, 0.08);
  border-radius: 0.4rem;
  transform: scaleY(0.85);
  transform-origin: 0% 0%;
}
</style>
