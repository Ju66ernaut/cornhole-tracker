<template>
  <div id="app">
    <div class="drag">
      <h2>1</h2>
      <draggable
        v-model="currentMatch.team1.players"
        class="dragArea"
        :options="{ group: 'people' }"
      >
        <div v-for="(p, index) in currentMatch.team1.players" :key="index">
          {{ p.name }}
        </div>
      </draggable>
      <h2>Players</h2>
      <draggable
        v-model="Players"
        class="dragArea"
        :options="{ group: 'people' }"
      >
        <div v-for="(p, index) in Players" :key="index">{{ p.name }}</div>
      </draggable>
      <h2>2</h2>
      <draggable
        v-model="currentMatch.team2.players"
        class="dragArea"
        :options="{ group: 'people' }"
      >
        <div v-for="(p, index) in currentMatch.team2.players" :key="index">
          {{ p.name }}
        </div>
      </draggable>
    </div>
  </div>
</template>

<script>
import Players from "./data/Players.js";
import DefaultMatch from "./data/Match.js";
import draggable from "vuedraggable";

export default {
  name: "App",
  components: {
    draggable
  },
  data() {
    return {
      Players,
      currentMatch: {}
    };
  },
  mounted() {
    this.currentMatch = { ...DefaultMatch };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.dragArea {
  min-height: 10px;
}
</style>
