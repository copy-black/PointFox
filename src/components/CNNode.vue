<template>
  <div id="cnnodeWrapper">
      <div>
             <span>cnnode论坛</span>
      </div>
   
    <div>
        <li v-for="(value,index2) in this.topicArr" :key="index2"> 
            <span>
                <img id="avatar" :src="value.author.avatar_url" alt="">
            </span>
            {{value.title}}
        </li>
    </div>
  </div>
</template>

<script>
import Axios from 'axios'
// vuedef
export default {
    data(){
        return{
            topicArr:[

            ]
        }
    },
    beforeCreate(){
        console.log('this is before')
    },
    //生命周期函数，钩子函数
    created(){
        let that =this;
        // 请求数据
        // console.log('this is vue');
        Axios.get('https://cnodejs.org/api/v1/topics').then(function(response){
                console.log(response)
                if(response.data.success){
                     that.topicArr=response.data.data;
                }
        })
    }
}
</script>

<style>

#avatar{
    width: 30px;
    height: 30px;
}
li{
    list-style: none;
}
</style>