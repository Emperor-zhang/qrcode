<template>
  <view class="content">
    <view class="getQrCode">
      <canvas canvas-id="qrcode" style="width: 354px;height: 354px;" />
    </view>
  </view>
</template>

<script>
import uQRCode from "@/static/js/uqrcode.js";

export default {
  data() {
    return {
      title: "Hello",
    };
  },
  onLoad() {
    this.make();
  },
  methods: {
    async make() {
      // 同步等待
      var res = await uQRCode.make({
        canvasId: "qrcode",
        componentInstance: this,
        text:
          "https://wb.jaas.ac.cn/Authorize/WxAuthorize.ashx?RedirectUrl=https://wb.jaas.ac.cn/KeTianXia.G.201109/index.html&snsapi=1",
        size: 354,
        margin: 10,
        backgroundColor: "#ffffff",
        foregroundColor: "#000000",
        fileType: "png",
        errorCorrectLevel: uQRCode.errorCorrectLevel.H,
      });
      console.log(res);
    },
    toJSON() {},
  },
};
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.canvas-hide {
  /* 1 */
  position: fixed;
  right: 100vw;
  bottom: 100vh;
  /* 2 */
  z-index: -9999;
  /* 3 */
  opacity: 0;
}
</style>
