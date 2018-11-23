<template>
  <div id="app">
      <HelloWorld/>
</div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "app",
  components: {
    HelloWorld
  },
  data: () => ({
  }),
  mounted: function() {
    this.getChampions();
  },
  watch: {
  },
  methods: {
    getChampions: function() {
      fetch("champions.json")
        .then(response => response.json())
        .then(response => {
          for (let champion in response.data) {
            this.champions.push(response.data[champion]);
          }
        })
        
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
