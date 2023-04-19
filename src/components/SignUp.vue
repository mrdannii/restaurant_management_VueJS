<template>
    <img alt="Vue logo" src="../assets/rest.png" height="200" width="200">
 <h1>Sign Up</h1>

 <div class="register">
    <input type="text" class="text" placeholder="User name" v-model="name">
    <input type="email" class="email" placeholder="Email" v-model="email">
    <input type="password" class="password" placeholder="Password" v-model="password">
    <button v-on:click="signup"> Sign Up </button>
 </div>
</template>

<script>
import axios from 'axios'
    export default{
        name:'SignUp',
        data(){
            return {name:"", email:"", password:""}
        },
        methods:{
            async signup(){
                let result=await axios.post("http://localhost:3000/users",{
                    email:this.email,
                    name:this.name,
                    password:this.password
                });
                if(result.status===201)
                {
                    alert('sign up')
                }
                localStorage.setItem("user-info",JSON.stringify(result.data)),
                this.$router.push({name:'HomePage'})
            }
        }
    }
</script>

<style>
.register input{
    width: 300px;
    height: 40px;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    display: block;
    padding-left: 10px;
    border: 1px solid gray;
}
.register button{
    width: 250px;
    height: 30px;
}
</style>