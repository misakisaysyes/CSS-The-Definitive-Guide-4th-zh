<template>
  <div class="figure">
    <div class="fg">
      <div class="fgimg">
        <iframe
          v-if="isHtml"
          :src="htmlSrc"
          ref="frame"
          seamless
          frameborder="0"
          scrolling="no"
          @load="frameAdapt"
        />
        <img v-if="!isHtml" :src="pngSrc" @click="jumpToHtml" />
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
import axios from "axios";

export default {
  props: ["figure", "type"],
  data() {
    return {
      pngSrc: "",
      htmlSrc: "",
      isHtml: false
    };
  },
  created() {
    this.chooseTip();
  },
  methods: {
    locateResources() {
      let tmp = this.figure.split("-");
      // if (this.type === "png") {
      //   this.isHtml = false;
      // } else {
      //   this.isHtml = true;
      // }

      // if (this.isHtml) {
      this.htmlSrc =
        "./htmlfigures/ch" + tmp[0] + "/fg" + this.figure + ".html";
      // } else {
      this.pngSrc = "./figures/ch" + tmp[0] + "/fg" + this.figure + ".png";
      // }
    },
    frameAdapt() {
      const frame = this.$refs.frame;
      const doc = frame.contentWindow.document.body;
      frame.width = doc.scrollWidth;
      frame.height = doc.scrollHeight;
      doc.style.margin = "0";
    },
    jumpToHtml() {
      axios
        .get(this.htmlSrc)
        .then(resp => {
          if (resp) {
            window.open(this.htmlSrc);
          }
        })
        .catch(e => {
          alert("抱歉，没有找到此图片对应的 HTML 页面！");
        });
    }
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
</style>