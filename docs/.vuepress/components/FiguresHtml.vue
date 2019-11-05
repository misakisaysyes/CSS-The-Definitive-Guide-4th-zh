<template>
  <div class="figure">
    <div class="fg">
      <div class="fgimg">
        <iframe
          id="bdIframe"
          :src="imgSrc"
          ref="frame"
          seamless
          frameborder="0"
          scrolling="no"
          @load="getFix"
        />
      </div>
    </div>
    <div class="fgtitle">
      <p>
        图 {{figure}}：
        <slot></slot>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["figure"],
  data() {
    return {
      imgSrc: "",
      fWidth: "",
      fHeight: ""
    };
  },
  created() {
    this.chooseTip();
  },
  mounted() {
    const oIframe = document.getElementById("bdIframe");
    const deviceWidth = document.documentElement.clientWidth;
    const deviceHeight = document.documentElement.clientHeight;
    oIframe.style.width = Number(deviceWidth) + "px"; //数字是页面布局宽度差值
    oIframe.style.height = Number(deviceHeight) + "px"; //数字是页面布局高度差
    // this.fWidth = this.$refs["frame"].contentWindow.document.body.clientWidth;
    // console.log("fWidth=" + this.fWidth);
    // this.fHeight = this.$refs["frame"].contentWindow.document.body.clientHeight;
    // console.log("fHeight=" + this.fHeight);
  },
  methods: {
    chooseTip() {
      let tmp = this.figure.split("-");
      this.imgSrc =
        "https://meyerweb.github.io/csstdg4figs/11-positioning/offset-props-lower-right.html";
    },
    getFix() {}
  }
};
</script>

<style scoped>
.fg {
  border-radius: 6px;
  border-width: 2px;
  border-style: solid;
  border-color: black;
  margin: 0 auto;
  width: 100%;
}
.fgimg {
  padding: 4px 24px 0;
}
.fgtitle {
  text-align: center;
  font-weight: bold;
}
iframe body {
  margin: 0;
}
</style>