<template>
  <div class="wechat">
    <h1>{{ msg }}</h1>
    <div>
      <label>当前地址：</label>
      <span>{{ url }}</span>
    </div>
  </div>
</template>

<script>
// import wx from 'weixin-js-sdk'

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
    const params = this.$route.query;
    const { code } = params;
    location.href = `https://mp.weixin.qq.com/mp/profile_ext?action=home&__biz=MzA5ODU3OTI5MQ==&scene=124&code=${code}#wechat_redirect`;
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
