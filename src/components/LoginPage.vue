<template>
  <div class="modal-overlay" @click.self="$emit('close')">
    <div class="white">
    <div class="modal-content">
      <div class="logincontain">
        <img alt="Vue logo" src="../assets/logo.svg" width="180" height="100" />
        <h1>Login</h1>
      </div>
      <form @submit.prevent="login">
        <div class="form-group">
          <label class="label" for="email">Email:</label>
          <input
            type="email"
            id="email"
            v-model="email"
            placeholder="Email"
            required
          />
        </div>
        <div class="form-group">
          <label for="password">Password:</label>
          <input
            type="password"
            id="password"
            v-model="password"
            placeholder="Password"
            required
          />
        </div>
        <div class="form-actions">
          <button type="submit">Login</button>
          <button type="button" @click="forgotPassword">Forgot Password</button>
        </div>
        <div class="sign-up">
          <p>
            Don't have an account?
            <a href="#" @click.prevent="signUp">Sign Up</a>
          </p>
        </div>
      </form>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: "LoginPage",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    login() {
      console.log("Login attempt with", this.email, this.password);
      alert(`Login attempt with ${this.email}`);
    },
    forgotPassword() {
      console.log("Forgot Password clicked");
      alert("Forgot Password");
    },
    signUp() {
      console.log("Sign Up clicked");
      alert("Redirect to Sign Up");
    },
  },
};
</script>

<style scoped>
.login-container {
  max-width: 400px;
  margin: 0 auto;
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 8px;
  
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.white{
  background-color: rgb(255, 255, 255);
  padding: 2rem;
  border-radius: 4%;
}

.logincontain {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 2rem;
}

.label {
  display: flex;
}



.form-group {
  margin-bottom: 1rem;
  justify-content: flex-start;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
}

.form-group input {
  width: 100%;
  padding: 0.5rem 0rem 0.5rem 0rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding-left: 0.3rem;
}

.form-actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 2rem 0rem 2rem 0rem;
}

.form-actions button {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.form-actions button:first-child {
  background-color: #007bff;
  color: white;
}

.form-actions button:last-child {
  background-color: #6c757d;
  color: white;
}

.sign-up {
  margin-top: 1rem;
  text-align: center;
}

.sign-up a {
  color: #007bff;
  text-decoration: none;
}

.sign-up a:hover {
  text-decoration: underline;
}
</style>


<!--<template>
  <div>
    <h1>Hello</h1>
    <p>{{ data }}</p>
    <button v-on:click="hello(`hello call`)">Call Hello fxn</button>
  </div>
</template>
<script>
export default {
  name: "HomePage",
  props: {
    data: String,
    msg: String,
  },
  methods: {
    hello(data) {
      console.log("hello console is called")
    // alert("hello")
    alert(data)
    },
  },
};
</script> -->
