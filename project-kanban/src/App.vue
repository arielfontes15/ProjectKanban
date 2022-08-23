<template>
    <div>
      <HeaderKanban></HeaderKanban>
      <div class="board">
        <div class="lane">
          <h2 class="lane-title"></h2>
        </div>
        <div class="lane">
          <h2 class="lane-title"></h2>
        </div>
        <div class="lane">
          <h2 class="lane-title"></h2>
        </div>
        <div class="lane">
          <h2 class="lane-title"></h2>
        </div>
      </div>
    </div>
</template>

<script>
import HeaderKanban from './components/HeaderKanban.vue'

export default {
  name: 'App',
  components: {
    HeaderKanban
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
  height: 15rem;
  border-radius: 0.8rem;
  box-shadow: 0 .1rem .2rem 0 rgba(33, 33, 33, .1);
  margin: 0 0.8rem;
}
</style>
