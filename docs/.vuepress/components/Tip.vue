<template>
  <div class="tip">
    <img :src="imgSrc">
    <span>
        <slot></slot>
    </span>
    <span>
        <slot name="translation"></slot>
    </span>
  </div>
</template>

<script>
export default {
  props: ["tips"],
  data() {
    return {
      imgSrc: ""
    };
  },
  created() {
    this.chooseTip();
  },
  methods: {
    chooseTip() {
      if (this.tips === "blue") {
        this.imgSrc = "./note.png";
      } else if (this.tips === "green") {
        this.imgSrc = "./tip.png";
      } else if (this.tips === "orange") {
        this.imgSrc = "./warn.png";
      }
    }
  }
};
</script>

<style scoped>
tip {
    width: 100%
}
img {
    width: 12%;
    float: left;
}
p { 
  overflow-wrap: break-word
}
</style>