<template>
        <div class="login">
            <v-card class="card">
                <v-card-title>
                    <v-avatar>
                        <v-icon>mdi-login</v-icon>
                    </v-avatar>
                    <h1>Login</h1>
                </v-card-title>
                <v-card-text>
                    <v-form @submit.prevent="submitHandler" ref="form">
                        <v-text-field v-model="email" :rules="emailRules" label="Email" prepend-inner-icon="mdi-account"
                            required></v-text-field>
                        <v-text-field :type="passwordShow ? 'text' : 'password'" v-model="password" :rules="passwordRules"
                            label="Password" prepend-inner-icon="mdi-key"
                            :append-icon="passwordShow ? 'mdi-eye' : 'mdi-eye-off'"
                            @click:append="passwordShow = !passwordShow" required></v-text-field>

                        <v-switch label="Remember Me" color="indigo">
                        </v-switch>


                    </v-form>
                </v-card-text>
                
                    <v-btn block elevation="8" @click="authenticate" :loading="loading" type="submit" color="indigo">
                        <span class="white--text px-8"> Login</span></v-btn>

                <div class="register">
                    <span>Don't have an account? </span><a href="http://localhost:8081/register" @click="$router.push('/Register')">Register</a>
                </div>

            </v-card>
        </div>
</template>
  
  
<script>



export default {
    name: 'LoginPage',


    data: () => ({
        loading: false,
        snackbar: false,
        passwordShow: false,
        email: '',
        emailRules: [
            v => !!v || 'E-mail is required',
            v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
        ],
        password: '',
        passwordRules: [
            v => !!v || 'Password is required',
            v => (v && v.length >= 6) || 'Password must be 6  characters or more!',
        ],
    }),
    methods: {
        authenticate() {
            alert('Login successful')
        },
        submitHandler() {
            if (this.$refs.form.validate()) {
                this.loading = true
                this.snackbar = true
                setTimeout(() => {
                    this.loading = false
                    // this.snackbar = true

                }, 1000)
            }
        }
    }
};

</script>
  
<style scoped>
.login {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-image: url('@/assets/img/login-bg.png');
    background-size: cover;
    background-position: center;
}

.card {
    background-color: rgba(255, 255, 255, 0.3);
    border-radius: 10px;
    box-shadow: 0 2px 6px rgba(212, 65, 65, 0.2);
    width: 400px;
    max-width: 100%;
    padding: 24px;
    margin-bottom: 24px;
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.2);
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.2), 0 5px 15px rgba(0, 0, 0, 0.1);
}

.card-title {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 24px;
}

.avatar {
    margin-right: 16px;
    background-color: #0f0e0e;
    color: #fff;
}

h1 {
    font-size: 2.5rem;
    margin: 0;
}

.v-input {
    width: 100%;
    margin-bottom: 24px;
}

.v-btn {
    width: 100%;
    margin-top: 24px;
    
    /* or any color of your choice */
    color: #080303;
    /* or any contrasting color to make the text readable */
    border-radius: 20px;
    /* or any value of your choice */
    text-transform: capitalize;
    /* or any other text transformation of your choice */
    font-weight: bold;
    /* or any font weight of your choice */
    transition: background-color 0.2s ease-in-out;
    /* add a smooth transition effect */
}

.v-btn:hover {
    background-color: #fff;
    /* or any color of your choice */
    color: #1a237e;
    /* or any contrasting color to make the text readable */
}

.card-title h1,
.v-input,
.v-switch,
.v-btn {
    font-family: 'Roboto', sans-serif;
    /* or any other font of your choice */
}

.v-input:focus:not(.v-textarea) {
    border-color: #1a237e;
    /* or any color of your choice */
    box-shadow: none;
    background-color: #f5f5f5;
    /* or any color of your choice */
}

.v-icon.mdi-eye:hover {
    color: #1a237e;
    /* or any color of your choice */
}

.v-snackbar {
    margin-bottom: 24px;
}

.register {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
    font-size: 14px;
    color: #0c0b0b;
}

.register span {
    margin-right: 5px;
}

.register a {
    color: #3913e0;
    text-decoration: none;
    font-weight: bold;
}

.register a:hover {
    text-decoration: underline;
}
</style>