<template>
  <div ref="tile" class="tile" v-on:click="click">
    {{ num }}
  </div>
</template>

<script>
export default {
  name: "Tile",
  data() {
    return {
      num: Math.floor(Math.random() * 5) + 2
    };
  },
  methods: {
    click: function() {
      if (this.$refs.tile.classList.contains("close")) {
        return;
      }
      this.$refs.tile.classList.add("close");
      this.$emit("tileclick", this.num);
      setTimeout(() => {
        this.num = Math.floor(Math.random() * 5) + 2;
        this.$refs.tile.classList.remove("close");
      }, 2000);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.tile {
  transition: opacity 0.3s ease 0s;
  width: 50px;
  height: 50px;
  background-color: wheat;
  font-size: 25pt;
  opacity: 1;
}
.tile.close {
  opacity: 0;
}
</style>
