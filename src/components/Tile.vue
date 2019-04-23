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
      num:
        Math.floor(Math.random() * (Number(this.max) - Number(this.min) + 1)) +
        Number(this.min)
    };
  },
  props: ["min", "max"],
  methods: {
    click: function() {
      if (this.$refs.tile.classList.contains("close")) {
        return;
      }
      this.$refs.tile.classList.add("close");
      this.$emit("tileclick", this.num);
      setTimeout(() => {
        this.num =
          Math.floor(
            Math.random() * (Number(this.max) - Number(this.min) + 1)
          ) + Number(this.min);
        this.$refs.tile.classList.remove("close");
      }, 2000);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.tile {
  transition: opacity 1s, transform 1s;
  width: 50px;
  height: 50px;
  background-color: wheat;
  font-size: 25pt;
  opacity: 1;
  transform: rotate(0deg) scale(1, 1);
}
.tile.close {
  opacity: 0;
  transform: rotate(360deg) scale(0.1, 0.1);
}
</style>
