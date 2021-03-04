<template>
  <div class="wechat">
    <!-- <h1>{{ msg }}</h1> -->
    <div>
      <!-- <label>当前地址：</label>
      <span>{{ url }}</span>
      <br/> -->
      <img src="qrcode.png" />
    </div>
  </div>
</template>

<script>
import wx from "weixin-js-sdk";

export default {
  name: "wechat",
  data() {
    return {
      msg: "微信公众号跳转中...",
      url: "",
    };
  },
  mounted() {
    this.url = location.href;
    alert(JSON.stringify(wx));
    try {
      wx.scanQRCode({
        needResult: 1, // 默认为0，扫描结果由微信处理，1则直接返回扫描结果，
        scanType: ["qrCode", "barCode"], // 可以指定扫二维码还是一维码，默认二者都有
        success: function(res) {
          var result = res.resultStr; // 当needResult 为 1 时，扫码返回的结果
          alert(result);
        },
      });
    } catch (err) {
      alert(JSON.stringify(err));
    }

    // const params = this.$route.query;
    // const { code } = params;
    // // location.href=`http://weixin.qq.com/r/jUNNVWrEdzcIrS429xaf${code}`;
    // location.href = `https://mp.weixin.qq.com/mp/profile_ext?action=home&__biz=MzA5ODU3OTI5MQ==&scene=124&code=${code}#wechat_redirect`;
    // try {
    //   const url = `https://mp.weixin.qq.com/mp/r/jUNNVWrEdzcIrS429xaf${code}`;
    //   // alert(url);

    //   location.url = url;
    // } catch (err) {
    //   alert(err);
    // }
    // try {
    //             alert(JSON.stringify( window.WeixinJSBridge));

    //   window.WeixinJSBridge.invoke(
    //     "openUrlByExtBrowser",
    //     {
    //       appID: "wx879145b190c1cc02",
    //       url: "http://weixin.qq.com/r/mRwYAELEPB9DrQZj90mL",
    //     },
    //     function(e) {
    //       alert(JSON.stringify(e));
    //     }
    //   );
    // } catch (err) {
    //   alert(err);
    // }
    // location.href = "https://weixin.qq.com/r/sh0QCJLEFs9prdZr90ig";
    // location.href =
    //   "https://mp.weixin.qq.com/mp/profile_ext?action=home&__biz=Mzg2MzUzMDU5Ng==#wechat_redirect";
  },
};
</script>
