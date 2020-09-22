<template>
  <div :style="setStyle()" class="animDiv">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "pulse",
  props: {
    pattern: {
      type: String,
      default: "rb",
    },
    speed: {
      type: Number,
      default: 10,
    },
  },
  data() {
    //make styles an object
    return {
      color: 0,
      color1: 0,
      color2: 255,
      position: 0,
      increasing: true,
      style: {},
    };
  },
  mounted() {
    setInterval(() => {
      this.colorMachine();
    }, this.speed);
  },
  methods: {
    setStyle() {
      return {
        background: this.getPattern(),
      };
    },
    getPattern() {
      if (this.pattern == "rb") {
        return `rgb(${this.color1}, 0, ${this.color2})`;
      } else if (this.pattern == "rg") {
        return `rgb(${this.color1}, ${this.color2}, 0)`;
      } else {
        return `rgb(0, ${this.color2}, ${this.color1})`;
      }
    },
    colorMachine() {
      if (this.increasing) {
        if (this.color1 >= 255) {
          this.increasing = false;
        } else {
          this.color1++;
          this.color2--;
        }
      } else {
        // color 1-- color 2++
        if (this.color1 <= 0) {
          this.increasing = true;
        } else {
          this.color1--;
          this.color2++;
        }
      }
    },
  },
};
</script>

<style>
.animDiv {
  background-position: relative;
  margin: auto;
}
.container {
  width: 50vw;
}
h1,
h2,
h3,
h4,
p {
  color: white;
  mix-blend-mode: difference;
}
</style>
