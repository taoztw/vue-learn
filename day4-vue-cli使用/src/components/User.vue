<template>
    <div>
        这是User组件
        <h3>用户列表</h3>
        <table border="2">
            <tr>
                <td>ID</td>
                <td>name</td>
                <td>birthday</td>
                <td>info</td>
                <td>operation</td>
            </tr>
            <tr v-for="user in users" :key="user.id">
                <td>{{user.id}}</td>
                <td>{{user.name}}</td>
                <td>{{user.birthday}}</td>
                <td>{{user.info}}</td>
                <td><a href="javascript:;" @click="delUser(user.id)">删除</a> | <router-link :to="`/detail/${user.id}`">详情</router-link></td>
            </tr>
        </table>


        <br>
        用户名：<input type="text" v-model="name"><br>
        生日：<input type="text" v-model="birthday"><br>
        详细信息：<input type="text" v-model="info"><br>
        <button @click="adduser">添加用户</button>
    </div>
</template>

<script>
export default {
    name: "User",
    data(){
        return {
            users: [
                {"id":1, name:'tz1',birthday:"2020-1-1",info:"tz1详细信息"},
                {"id":2, name:'tz2',birthday:"2020-1-1",info:"tz2详细信息"},
                {"id":3, name:'tz3',birthday:"2020-1-1",info:"tz3详细信息"},
            ],
            name:"",
            birthday:"",
            info:""
        }
    },
    methods:{
        adduser(){
            // console.log(this.users.length)
            let len = this.users.length + 1
            let tmp = {id:len, name:this.name, birthday:this.birthday,info:this.info}
            this.users.push(tmp)
        },
        delUser(index){
            // index = index-1
            // console.log(index)
            this.users.splice(index-1,1)
            // console.log(this.users[index]);
        }
    }
}
</script>

<style scoped>

</style>
