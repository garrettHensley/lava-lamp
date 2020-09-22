<template>
  <div>
    <lava-lamp
      speed="5"
      pattern="gb"
      style="border-radius: 0em; padding: .5em; text-align: center;"
      class="container"
    >
      <h1>Animated Lava Lamp Container</h1>
      <p class="lead">
        A beautifuly animated container for your projects. Includes customizable
        options such as speed, and colors to cycle through.
      </p>
    </lava-lamp>
  </div>
</template>

<script>
import LavaLamp from "@/components/LavaLamp.vue";

export default {
  components: {
    LavaLamp,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap");
html body {
  background-color: rgb(54, 54, 54);
}
* {
  font-family: "Lato", sans-serif;
}
h1 {
  font-size: 5em;
  font-weight: 100;
}
h1,
h2,
h3,
h4,
p {
  color: white;
  mix-blend-mode: luminosity;
}
.lead {
  font-size: 1.5em;
  font-weight: 300;
}
</style>
