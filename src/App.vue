
<template>
  <div >
	<h1>Witaj w systemie do zapisów na zajęcia</h1>
    <div v-if="authenticatedUsername">
      <h2>Witaj {{ authenticatedUsername }}!
        <a @click="logout()" class="float-right  button-outline button">Wyloguj</a>
      </h2>
      <meeting-page :username="authenticatedUsername"></meeting-page>
    </div>
    <div v-else>
      <login-form @login="login($event)"></login-form>
    </div>
  </div>
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import MeetingPage from "./meetings/MeetingPage";

    export default {
        components: {LoginForm, MeetingPage},
        data() {
            return {
                authenticatedUsername: ""
            };
        },
        methods: {
            login(user) {
                this.authenticatedUsername = user.login;
            },
            logout() {
                this.authenticatedUsername = '';
            }
        }
    };
</script>


 