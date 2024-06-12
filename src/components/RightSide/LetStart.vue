<template>
  <div class="aligncenter">
    <div class="contain">
      <div class="rightbar">
        <img alt="Vue logo" src="../../assets/rocket.png" height="66" />
        <h1>Let's get started!</h1>
        <p class="para">Please provide your billing address.</p>
      </div>

      <form @submit.prevent="proceedToNextPage">
        <div class="form-group">
          <div class="flex">
            <div class="column">
              <label
                class="label"
                for="email"
                style="width: 100%; display: flex"
                >First Name</label
              >
              <input
                type="name"
                id="firstname"
                v-model="firstname"
                placeholder="First Name"
                required
              />
            </div>
            <div class="column">
              <label
                class="label"
                for="password"
                style="width: 100%; display: flex"
                >Last Name</label
              >
              <input
                type="lastname"
                id="lastname"
                v-model="lastname"
                placeholder="Last Name"
                required
              />
            </div>
          </div>
          <label class="label" for="email" style="width: 100%; display: flex"
            >Billing address</label
          >
          <input
            type="address"
            id="address"
            v-model="address"
            placeholder="1234 queen address"
            required
          />

          <div class="flex">
            <div class="column">
              <label
                class="label"
                for="email"
                style="width: 100%; display: flex"
                >Postal Code</label
              >
              <input
                type="postal"
                id="postal"
                v-model="postal"
                placeholder="Postal Code"
                required
              />
            </div>
            <div class="column">
              <label
                class="label"
                for="password"
                style="width: 100%; display: flex"
                >Province</label
              >
              <input
                type="province"
                id="province"
                v-model="province"
                placeholder="Province"
                required
              />
            </div>
          </div>

          <label class="label" for="password" style="width: 100%; display: flex"
            >Phone Number</label
          >
          <input
            type="phonenumber"
            id="number"
            v-model="number"
            placeholder="Phone Number"
            required
          />
        </div>
        <div class="form-actions">
          <button class="next-button" type="submit">Next</button>
        </div>
      </form>
    </div>
  </div>
</template>
<script></script>

<style scoped>
h1 {
  color: #2e6666;
  margin: 0;
  padding: 0;
}

.aligncenter {
  display: flex;
  justify-content: center;
  width: 100%;
}

.para {
  color: rgb(143, 143, 143);
  margin-top: 10px;
  margin-bottom: 80px;
}
.contain {
  display: flex;
  flex-direction: column;
  justify-content: center;

  /* padding: 0 80px 0 160px; */
}

.rightbar {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 100%;
}
.flex {
  display: flex;
  justify-content: space-between;
}

.column {
  width: 48%; /* Adjust the width as needed */
  display: flex;
  flex-direction: column;
}

.label {
  margin-bottom: 8px;
  font-size: 16px;
}

input {
  padding: 12px;
  font-size: 16px;
  margin-bottom: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
  box-sizing: border-box;
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
  padding: 0.6rem 0.4rem 0.6rem 0.4rem;
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
  padding: 0.8rem 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  color: white;
  background-color: #2e6666;
  width: 100%;
}

.next-button {
  padding: 4px;
}
</style>

<!--<template>
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
    name: "LetStart",
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
  -->
