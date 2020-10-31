<template>
    <div>
        {{ username }}
        <my-input
            name="Username"
            :rules="{ required: true, min: 5}"
            type="text"
            :value="username.value"
            @update="update"
        />

        {{ password }}
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
            valid: true,
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
    methods: {
        update(payload){
            console.log(payload);
            this[payload.name.toLowerCase()].value = payload.value
        }
    }
} 
</script>
 
<style>
body{
    font-family: Arial, Helvetica, sans-serif;
}
</style>
