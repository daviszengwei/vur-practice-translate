<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单 / 便捷 / 快速</h5>
    <translate-form v-on:formSubmit="translateText"></translate-form>
    <translateOut v-text="translated"></translateOut>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import translateOut from './components/TranslateOut'

export default {
  name: 'App',
  data () {
    return {
      translated:""
    }
  },
  components: {
    TranslateForm,translateOut
  },
  methods: {
    translateText:function(text,language){
      this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190410T093102Z.88858140a7af33b1.2e7a578010f779b3ab1855de315d9c9015a49829&text="+text+"&lang="+language)
        .then((response)=>{
           console.log(response.body.text[0])
           this.translated = response.body.text[0]
        })
    }
  },  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
