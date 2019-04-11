<template>
  <div id="translate-form">
    <form v-on:submit="submitForm">
        <input type="text" v-model="transText" placeholder="请输入需要查询的内容">
        <select v-model="language">
            <option value="en">English</option>
            <option value="ko">Korean</option>
            <option value="ru">Russian</option>
            <option value="ja">Japanese</option>
        </select>
        <button>翻译</button>
    </form>
  </div>
</template>

<script>


export default {
  name: 'translate-form',
  data () {
      return {
          transText:"",
          language:""
      }
  },
  methods: {
      submitForm:function(e){
        // alert(this.transText);
        this.$emit("formSubmit",this.transText,this.language)
        e.preventDefault();//页面不会刷新
        

      }
  },
  created:function(){
      this.language = "en"
  }
}
</script>

<style>

</style>