<template>
  <div id="app">
    <div class="ui container">
      <h1>彦祖翻译通
        <small class="sub-title">准确, 高效, 便捷</small>
      </h1>
      <div class="ui divider"></div>
      <translate-form v-on:formSubmit="translateText"></translate-form>
      <translate-out-put v-text="result" v-bind:isShow="isShow"></translate-out-put>
    </div>
  </div>

</template>

<script>
  import TranslateForm from './components/TranslateForm'
  import TranslateOutPut from './components/TranslateOutPut'
  import md5 from 'js-md5'

  export default {
    name: 'App',
    components: {TranslateForm, TranslateOutPut},
    data() {
      return {
        result: '',
        isShow: false
      }
    },
    methods: {
      translateText(text, language) {

        // 构造url
        let appid = '20180320000138068';
        let key = 'mblZKRkMGrDUXgGMjmT1';
        let salt = (new Date).getTime();
        let query = text;
        let from = 'auto';
        let to = language;
        let str = appid + query + salt + key;
        let sign = md5(str);
        let url = 'http://api.fanyi.baidu.com/api/trans/vip/translate?' +
          'q=' + query + '&appid=' + appid + '&salt=' + salt
          + '&from=' + from + '&to=' + to + '&sign=' + sign

        // 请求
        this.$http.jsonp(url)
          .then(response => {
            this.result = response.body.trans_result[0].dst
            this.isShow = true
          })
      }
    }
  }
</script>

<style>
  #app {
    color: #25374a;
    margin-top: 60px;
  }

  .sub-title {
    font-size: 14px;
    margin-left: 12px;
    color: #3b546b;
  }
</style>
