<template>
  <form @submit.prevent="enter()">
    <label>Login</label>
    <input type="text" v-model="user.login">
    
    <button type="submit">{{ labelOfTheButton }}</button>
  </form>
</template>

<script>
    export default {
        props: ["buttonLabel"],
        data() {
            return {
                user: {}
            };
        },
        methods: {
            enter() {
                this.$emit("login", this.user);
            }
        },
        computed: {
            labelOfTheButton() {
                return this.buttonLabel || 'Zaloguj się';
            }
        }
    };
</script>



