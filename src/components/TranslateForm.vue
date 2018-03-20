<template>
  <div class="ui segment">
    <div class="row" id="translateForm">
      <div class="col-md-12">
        <form class="ui form" action="">

          <div class="fields">

            <div class="six wide field">
              <label for="">查词</label>
              <input v-model="textToTranslate" type="text" placeholder="输入翻译内容">
            </div>

            <div class="ten wide field">
              <label for="">语言</label>
              <select @change="formSubmit" class="ui fluid dropdown" v-model="language">
                <option value="en">英语</option>
                <option value="yue">粤语</option>
                <option value="jp">日语</option>
                <option value="kor">韩语</option>
                <option value="ru">俄语</option>
                <option value="vie">越南语</option>
                <option value="dan">丹麦语</option>
                <option value="it">意大利语</option>
              </select>
            </div>

          </div>

          <div class="field">
            <button @click="formSubmit" class="ui animated blue fluid button">
              <span class="visible content">查词</span>
              <span class="hidden content">
              <span>fanyi.gengwenhao.com</span>
            </span>
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'translate-form',
    data() {
      return {
        textToTranslate: '',
        language: 'en'
      }
    },
    methods: {
      formSubmit(e) {
        e.preventDefault()

        let text = this.textToTranslate
        if (text != '') {
          this.$emit('formSubmit', text, this.language)
        }
      }// end forSubmit
    }
  }
</script>

<style scoped>
  .field {
    margin-top: 15px !important;
  }

  input[type=submit] {
    margin-top: 25px;
  }
</style>
