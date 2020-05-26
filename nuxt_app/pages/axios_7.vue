<!-- 削除の処理 -->
<template>
    <section class="container">
        <h1>{{title}}</h1>
        <p>{{message}}</p>
        <table>
            <tr>
                <th>Email</th>
                <td><input v-model="email"></td>
                <td><button @click="delData">Click</button></td>
            </tr>
        </table>
        <hr>
        <!-- データを一覧表示 -->
        <ul v-for="(data, key) in json_data">
            <li><strong>{{key}}</strong><br>{{data}}</li>
        </ul>
    </section>
</template>

<script>
  const axios = 　require('axios')
  let url = "https://funeace-sample-vue.firebaseio.com/person"
export default {
    data: function(){
        return {
            title:'Axios',
            email:'',
            message:'axios sample.',
            json_data:{},
        };
    },
    methods: {
        delData: function() {
            let del_url = url + '/' + this.email + '.json';
            // 削除の処理
            axios.delete(del_url).then((re)=>{
                this.message = this.email + 'を削除しました。';
                this.email = '';
                this.getData();
            });
        },
        getData: function() {
            axios.get(url + '.json').then((res) => {
                this.json_data = res.data;
            }).catch((error)=>{
                this.message = 'ERROR!';
                this.json_data = {};
            });
        }
    },
    created: function(){
        this.getData();
    }
}
</script>