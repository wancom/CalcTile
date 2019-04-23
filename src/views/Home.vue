<template>
  <div ref="home" class="home">
    Question:{{ reqnum }}<br />
    Clicked Number:{{ nums }}
    <table align="center">
      <tr v-for="n in 6" v-bind:key="n">
        <td v-for="n in 6" v-bind:key="n">
          <Tile v-on:tileclick="tileclick" min="2" max="6" />
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
// @ is an alias to /src
import Tile from "@/components/Tile.vue";

export default {
  name: "home",
  components: {
    Tile
  },
  data() {
    return {
      nums: "",
      sum: 0,
      reqnum: Math.floor(Math.random() * 10) + 15
    };
  },
  methods: {
    tileclick: function(num) {
      console.log(num);
      this.sum += num;
      if (this.sum == this.reqnum) {
        console.log("OK");
        this.reqnum = Math.floor(Math.random() * 10) + 15;
        this.nums = "";
        this.sum = 0;
        document.bgColor = "lightcyan";
        setTimeout(() => {
          document.bgColor = "";
        }, 2000);
      } else if (this.sum > this.reqnum) {
        console.log("NG");
        this.reqnum = Math.floor(Math.random() * 10) + 15;
        this.nums = "";
        this.sum = 0;
        document.bgColor = "lightpink";
        setTimeout(() => {
          document.bgColor = "";
        }, 2000);
      } else {
        this.nums += num + "+";
      }
    }
  }
};
</script>

<style scoped>
.home {
  text-align: center;
}
</style>
