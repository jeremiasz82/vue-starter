<template>
   <div>
        <h1>Witaj w systemie do zapisów na zajęcia</h1>
        
          
        <div v-if="authenticatedUsername">
            <h2>Witaj {{ authenticatedUsername }}</h2>
            <a @click="logMeOut()">Wyloguj</a>
            <h4>dodaj spotkanie</h4>
            <meeting-page @meeting="addNewMeeting($event)"></meeting-page>
        </div>
        <div v-else>
            <login-form @login="logMeIn($event)" button-label="Wejdź"></login-form>
          
             
        </div>
     
        
		
   </div>

  
    
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import MeetingPage from "./meetings/MeetingPage";

    export default {
        components: {LoginForm,MeetingPage},
        data() {
            return {
                authenticatedUsername: '',
                meeting:'',
            }
        },
        methods: {
            logMeIn(username) {
                this.authenticatedUsername = username;
            },
            logMeOut() {
                this.authenticatedUsername = '';
            }
        }   
    }
 
</script>
<!-- <script>
    import "milligram";
    import MeetingPage from "./meetings/MeetingPage";

    export default {
        components: {MeetingPage},
        data() {
            return {
                meeting: '',
            }
        },
        methods: {
            NewMeeting(meeting) {
                this.meeting = meeting;
            },

        }
    }
</script> -->
