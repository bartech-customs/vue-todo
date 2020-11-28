<template>
  <div
    ref="heading"
    class="grey--text text--lighten-1 text-center container card pa-6"
  >
    <h1 class="mb-6 display-3 font-weight-bold">About</h1>
    <p class="display-1">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cumque, animi?
      Reiciendis at modi officiis sed aperiam repellat hic, sunt quia quasi ab
      dolor nihil a numquam, facilis quos, in consequatur!
    </p>

    <p class="display-1">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cumque, animi?
      Reiciendis at modi officiis sed aperiam repellat hic, sunt quia quasi ab
      dolor nihil a numquam, facilis quos, in consequatur!
    </p>
    <v-card elevation="7"
      ><v-img
        lazy-src="../assets/img/backg.webp"
        src="../assets/img/todo.jpg"
        height="400"
      ></v-img
    ></v-card>
  </div>
</template>

<script>
import gsap from "gsap";
export default {
  mounted() {
    let heading = this.$refs.heading;
    console.log(heading);
    gsap.from(heading, { opacity: 0.5, x: 100, duration: 1 });
  },
};
</script>

<style lang="scss" scoped></style>
