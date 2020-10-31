<template>
    <form @submit.prevent="submit" class="form">
        <div>
            <my-input
                name="Username"
                :rules="{ required: true, min: 5}"
                type="text"
                :value="username.value"
                @update="update"
            />

            <my-input
                name="Password"
                :rules="{ required: true, min: 10}"
                type="password"
                :value="password.value"
                @update="update"
            />
            
            <my-button 
                color="white"
                background="darkslateblue"
                :disabled="!valid"
            />
        </div>
    </form>
</template>

<script>
import MyButton from './MyButton.vue';
import MyInput from './MyInput.vue';

export default{
    components: {
        MyButton,
        MyInput
    },
    data(){
        return {
            username: {
                value: '',
                valid: false
            },
            password: {
                value: '',
                valid: false
            }
        }
    },
    computed:{
        valid(){
            return this.username.valid && this.password.valid
        }
    },
    methods: {
        submit($evt){
            console.log('Submitted');
        },
        update(payload){
            this[payload.name.toLowerCase()] = {
                value: payload.value,
                valid: payload.valid
            }
        }
    }
} 
</script>
 
<style>
body{
    font-family: Arial, Helvetica, sans-serif;
}
.form{
    max-width: 400px;
    width: 50%;
}
</style>
