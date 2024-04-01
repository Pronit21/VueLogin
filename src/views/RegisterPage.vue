<template>
  <div class="register">
    <v-card class="card" >
      <v-card-title>
        <v-avatar>
          <v-icon>mdi-account</v-icon>
        </v-avatar>
        <h1>Register</h1>
      </v-card-title>
      <v-card-text>
        <v-form v-model="valid">
          <v-text-field v-model="name" :rules="nameRules" label="Name" prepend-inner-icon="mdi-account-outline"
            required></v-text-field>
          <v-text-field v-model="email" :rules="emailRules" label="Email" prepend-inner-icon="mdi-email" required></v-text-field>
          <v-text-field v-model="password" :rules="passwordRules" label="Password" type="password"
            prepend-inner-icon="mdi-lock" :append-icon="passwordShow ? 'mdi-eye' : 'mdi-eye-off'"
            @click:append="passwordShow = !passwordShow" required></v-text-field>
          <v-text-field v-model="confirmPassword" :rules="confirmPasswordRules" label="Confirm Password" type="password"
            prepend-inner-icon="mdi-lock-check"
            :append-icon="passwordShow ? 'mdi-eye' : 'mdi-eye-off'"
            @click:append="passwordShow = !passwordShow" required></v-text-field>
            <v-btn block elevation="8" @click="authenticate" :loading="loading" type="submit" color="indigo">
                        <span class="white--text px-8"> Register</span></v-btn>

        </v-form>
      </v-card-text>

      <div class="login">
                    <span>Have an account? </span><a href="http://localhost:8081" @click="$router.push('/Register')">Login</a>
                </div>

    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      password: '',
      confirmPassword: '',
      valid: false,
      emailRules: [
        (v) => !!v || 'Email is required',
        (v) => /.+@.+\..+/.test(v) || 'Email must be valid',
      ],
      passwordRules: [
        (v) => !!v || 'Password is required',
        (v) => v && v.length >= 8 || 'Password must be at least 8 characters',
      ],
      confirmPasswordRules: [
        (v) => !!v || 'Confirm Password is required',
        (v) => v === this.password || 'Confirm Password must match Password',
      ],
      passwordShow: false,
    };
  },
  methods: {
    register() {
        window.location.href = 'http://localhost:8081/';
      },
      submitHandler() {
        if (this.$refs.form.validate()) {
          this.loading = true;
          this.snackbar = true;
          setTimeout(() => {
            this.loading = false;
            // this.snackbar = true
        }, 1000)
        }
      }
    }
};
</script>

<style>
.register {
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
    color: #3a2ed6;
}

.v-input {
    width: 100%;
    margin-bottom: 24px;
}

.v-input__icon--prepend {
  color: indigo;
}

.v-btn {
  width: 100%;
    margin-top: 24px;
    
    /* or any color of your choice */
    color: #cb2828;
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



.login {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
    font-size: 14px;
    color: #0c0b0b;
}

.login span {
    margin-right: 5px;
}

.login a {
    color: #3913e0;
    text-decoration: none;
    font-weight: bold;
}

.login a:hover {
    text-decoration: underline;
}


</style>
