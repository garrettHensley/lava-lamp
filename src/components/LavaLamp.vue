<template>
  <div :style="setStyle()" class="animDiv">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "lava-lamp",
  props: {
    pattern: {
      type: String,
      default: "rb",
    }, //
    speed: {
      type: Number,
      default: 10,
    },
    rotate: {
      type: Boolean,
      default: false,
    },
    lowerLim: {
      type: Number,
      default: 0,
    },
    higherLim: {
      type: Number,
      default: 256,
    },
  },
  data() {
    //make styles an object
    return {
      color1: this.lowerLim,
      color2: this.higherLim,
      deg: 45,
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
      // deg in constant rotation / incrementation
      if (this.pattern == "rb") {
        return `linear-gradient( ${this.deg}deg, rgb(${this.color1}, 0, ${this.color2}), rgb(${this.color2}, 0, ${this.color1}))`;
      } else if (this.pattern == "rg") {
        return `linear-gradient( ${this.deg}deg, rgb(${this.color1}, ${this.color2}, 0), rgb(${this.color2}, ${this.color1}, 0))`;
      } else if (this.pattern == "gb") {
        return `linear-gradient( ${this.deg}deg, rgb(0, ${this.color1}, ${this.color2}), rgb(0, ${this.color2}, ${this.color1}))`;
      }
    },
    colorMachine() {
      if (this.increasing) {
        console.log(this.increasing);
        if (this.color1 >= this.higherLim) {
          this.color1 = this.higherLim - 1;
          this.increasing = false;
        } else {
          this.color1++;
          this.color2--;
        }
      } else {
        console.log(this.increasing);
        if (this.color1 <= this.lowerLim) {
          this.color1 = this.lowerLim + 1;
          this.increasing = true;
        } else {
          this.color1--;
          this.color2++;
        }
      }
      if (this.rotate) {
        this.deg++;
      }
    },
  },
};
</script>

<style>
.animDiv {
  background-position: absolute;
  margin: auto;
  -webkit-box-shadow: 10px 10px 0px -5px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 10px 10px 0px -5px rgba(0, 0, 0, 0.75);
  box-shadow: 10px 10px 0px -5px rgba(0, 0, 0, 0.75);
}
.container {
  width: 50vw;
}
</style>
