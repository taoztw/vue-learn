<template>
    <div id="app">
<!--        绑定msg变量-->
        <input type="text" v-model="msg">
        <button @click="add_note">添加留言</button>

        <ul>
<!--            遍历msg-->
            <li v-for="(note, index) in msg_list" :key="index"><span>{{note}}</span>
            <a href="javascript:;" @click="delNote(index)">删除</a>
            </li>
        </ul>
        <br>
        <span>留言总数量：{{msg_list.length}}条</span>
        <input v-if="showFlag" type="button" value="删除所有" @click="delAll">
<!--        测试区域：-->
<!--        {{showFlag}}-->
    </div>
</template>

<script>
export default {
    name: "Home",
    data:function (){
        return {
            msg: "",
            msg_list: localStorage.msgs ? JSON.parse(localStorage.msgs) : [],
            showFlag: true
        }
    },
    methods: {
        add_note() {
            let msg = this.msg;
            if (msg){
                this.msg_list.push(this.msg);
                localStorage.msgs = JSON.stringify(this.msg_list);
                this.msg = "";
                this.showFlag = true
            }
        },
        delNote(index){
            this.msg_list.splice(index, 1);
            localStorage.msgs = JSON.stringify(this.msg_list);
            if(!this.msg_list.length){
                // console.log('test')
                this.showFlag = false
            }
        },
        delAll(){
          this.msg_list = [];
          localStorage.msgs = JSON.stringify(this.msg_list);
          this.showFlag = false
        },
    },
    beforeMount() {
        console.log('test')
        if(!this.msg_list.length){
            // console.log('test')
            this.showFlag = false
        }
    }
}
</script>

<style scoped>

</style>
