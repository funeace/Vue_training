<template>
  <div class="hello">
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
    <hr>
    <div>Value:
      <input type="number" v-model="val">
    </div>
    <div>Answer
      {{ answer }}
    </div>
  </div>
</template>

<script>
  export default {
    name: 'FizzBuzz',
    props: {
      title: String,
    },
    data:function(){
      return {
        message: "数字をにゅうりょくしてください",
        val: 0
      }
    },

    // watchを使えば値の変更に沿ってデータが書き換わってくれる
    watch:{
      val: function(value){
        this.val = value
        var val = parseInt(value)
        if(val % 15 == 0){
          this.answer = "FizzBuzz"
        }else if(val % 3 == 0){
          this.answer = "Fizz"
        }else if(val % 5 == 0){
          this.answer = "Buzz"
        }else{
          this.answer = val
        }
      }
    },
    created: function(){
      this.val = 1;
    },
  }
</script>