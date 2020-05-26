<template>
  <section class="container">
    <h1>{{title}}</h1>
    <p>{{message}}</p>
    </div>
  </section>
</template>


<script>
import firebase from "firebase";


export default {
  data: function(){
    return {
      title:'Auth',
      message: 'this is message.',
    };
  },
  created:function(){
    var config = { // ●各自の設定を記述
        apiKey: "AIzaSyBWNAxH6UpF4aWjG1ncWQMnBAJiw7814Pg",
        authDomain: "funeace-sample-vue.firebaseapp.com",
        databaseURL: "https://funeace-sample-vue.firebaseio.com",
        projectId: "funeace-sample-vue",
        storageBucket: "funeace-sample-vue.appspot.com",
        messagingSenderId: "788069287979"
    };
    firebase.initializeApp(config);


    var provider = new firebase.auth.GoogleAuthProvider();
    var self = this;
    firebase.auth().signInWithPopup(provider)
      .then(function(result) {
        self.message = result.user.displayName + ', ' 
          + result.user.email;
      });
  },
};
</script>
