<template>
    <div id="container">
        <v-layout align-center justify-center column fill-height>
            <v-row>
                <v-col cols="8" sm="6" md="4" lg="2">
                    <v-card class="vcard" max-width="1024px" color="#f6b092">
                        <v-img class="img" :src="require('@/assets/qna.png')"></v-img>
                        <v-card-text class="vcardtext">
                            <v-text-field class="text-field" v-model="email" label="E-mail" placeholder="Enter E-mail"
                                required></v-text-field>
                            <v-text-field class="text-field" v-model="password" label="Password"
                                placeholder="Enter Password" :type="'password'" required>
                            </v-text-field>
                        </v-card-text>
                        <v-card-actions class="vcardaction">
                            <v-btn type="text" rounded color="" class="btn" @click="submitLogin">L O G I N</v-btn>
                        </v-card-actions>
                        <div class="custom-error">
                            <p v-if="errors.length">
                                <b>Please correct the following error(s):</b>
                            <ul>
                                <li v-for="error in errors" :key="error">{{ error }}</li>
                            </ul>
                            </p>
                        </div>
                    </v-card>
                </v-col>
            </v-row>
        </v-layout>
    </div>
</template>

<script>
import { mapActions } from 'vuex';

export default {
    name: 'login',
    data() {
        return {
            errors: [],
            password: '',
            email: ''
        }
    },
    methods: {
        ...mapActions('user', {
            login: 'login'
        }),

        submitLogin(e) {
            this.errors = [];

            if (!this.email) {
                this.errors.push('Email required.');
            }
            if (!this.password) {
                this.errors.push('Password required.');
            }

            e.preventDefault();

            this.login({
                email: this.email,
                password: this.password
            })
                .then(response => {
                    if (this.$store.state.user.loggedIn) {
                        this.$router.replace('/')
                        location.reload()
                    }
                }, error => {
                    this.errors.push(error.message);
                })
        }
    }
}
</script>

<style scoped>
.img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 75%;
}

.vcard {
    font-family: "Gotham Medium", Helvetica, Arial;
    padding: 25px 25px 25px 25px;
    color: white;
    display: block;
    margin-left: auto;
    margin-right: auto;
}

.vcardaction {
    justify-content: center;
    align-items: center;
}

.btn {
    background: rgb(255, 255, 255);
}

.text-field {
    padding: 10px 10px 10px 10px;
    color: rgb(0, 0, 0);
}

.vcardtext {
    color: rgb(0, 0, 0);
}

#container {
    font-family: "Gotham Medium", Helvetica, Arial;
    margin: 3rem auto;
    padding: 5rem;
    max-width: 1200px;
    color: rgb(0, 0, 0);
}

.vrow {
    justify-content: center;
    margin-right: 50%;
    padding-left: 5%;
    height: 100%;
    width: 100%;
    font-size: 15px;
    font-weight: 600;
}

.custom-error {
    margin-top: 10px;
}

.custom-error p {
    color: red
}
</style>
