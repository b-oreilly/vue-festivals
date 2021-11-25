<template>
    <b-col>
        <div v-if="!loggedIn">
            <b-form>
                <b-form-group label="Email">
                    <b-form-input type="email" placeholder="Enter email address" v-model="form.email" />
                </b-form-group>
                <b-form-group label="Password">
                    <b-form-input type="password" placeholder="Enter password" v-model="form.password" />
                </b-form-group>
                <b-button v-on:keyup.enter="login()" @click="login()">Login</b-button>
            </b-form>
        </div>
        <p v-else>You are logged in :)</p>
    </b-col>
</template>

<script>
    import axios from 'axios';

    export default {
        name: "Login",
        components: {

        },
        props: {
            loggedIn: Boolean
        },
        data() {
            return {
                form: {
                    email: "",
                    password: ""
                }
            }
        },
        methods: {
            login() {
                axios
                    .post('https://festivals-api.herokuapp.com/api/users/login', {
                        email: this.form.email,
                        password: this.form.password
                    })
                    .then(response => {
                        console.log(response.data.token)
                        this.loggedIn = true
                        this.$emit('login')
                    })
                    .catch(error => {
                        console.log(error)
                        console.log(error.response.data.message)
                    })
            }
        }
    };
</script>