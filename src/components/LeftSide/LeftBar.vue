<template>
  <div class="sidebar">
    <div class="contain">
      <img alt="Vue logo" src="../../assets/truck.png" height="86" />
    </div>
    <div class="progressbar">
      <h1 class="head">
        Welcome to <br />
        Reach!
      </h1>
    </div>
  </div>
</template>

<script scoped>
export default {
  name: "LeftBar",
  methods: {
    selectMode(mode) {
      this.$emit("modeSelected", mode);
    },
  },
};
</script>

<style scoped>
h1 {
  color: #000000
}
.sidebar {
  width: 100%;
  display: flex;
  flex-direction: row;
}


.contain {
  display: flex;
  justify-content: start;
  margin-bottom: 160px;
}

.side-contain {
  margin: 20px;
  padding: 0px;
  font-size: 14px;
}

.head {
  margin: 0px;
  justify-content: start;
}
.progressbar {
  gap: 0px;
  display: flex;
  justify-content: start;
  align-items: start;
  font-size: 28px;
  font-weight: bolder;
}
</style>

<!--<template>
  <div>
    <div class="topbar">
      <ul>
        <li>About Us</li>
        <li>My Account</li>
        <li>Wishlist</li>
        <li>Order Tracking</li>
      </ul>
      <div class="flex">
        <p>Need help? Call Us:<span class="green"> + 1800 900 </span></p>
        <p>English</p>
        <p>USD</p>
      </div>
    </div>
    <div class="navbutton">
      <div class="navbar">
        <div class="contain">
          <img
            alt="Vue logo"
            src="../assets/logo.svg"
            width="180"
            height="100"
          />
        </div>
        <div class="all-categories">
          <h4>All Categories</h4>
        </div>
      </div>
      <div class="buttons">
        <button v-on:click="showLoginModal" class="buttonlogin">Login</button>
        <button class="buttonsignup">Sign Up</button>
      </div>
    </div>

    <LoginPage  v-if="isLoginModalVisible" @close="closeLoginModal" />
  </div>
</template>

<script>
import LoginPage from './LoginPage.vue';

export default {
  name: "HelloWorld",
  components: {
    LoginPage,
  },
  data() {
    return {
      isLoginModalVisible: false,
    };
  },
  methods: {
    showLoginModal() {
      this.isLoginModalVisible = true;
    },
    closeLoginModal() {
      this.isLoginModalVisible = false;
    },
  },
};
</script>

<style scoped>
/* Existing styles */
.topbar {
  color: #7e7e7e;
  font-size: 14px;
  display: flex;
  justify-content: space-between;
  border-bottom: 0.1rem solid #d8d8d8;
}
.navbutton {
  display: flex;
  justify-content: space-between;
}
.flex {
  display: flex;
  gap: 1rem;
}
.green {
  color: #42b983;
}
.navbar {
  display: flex;
}
.all-categories {
  border: 0.16rem solid #a4d8c1;
  padding: 0;
  border-radius: 5%;
  margin: 1.7rem;
  margin-left: 5rem;
}
h3 {
  display: flex;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.buttons {
  display: flex;
  align-items: center;
  gap: 1rem;
}
.buttonlogin {
  background-color: #3bb77e;
  border: 0em;
  border-radius: 8%;
  color: rgb(255, 255, 255);
  font-size: 16px;
  padding: 0.76rem 2.4rem;
}
.buttonsignup {
  background-color: #3bb77e;
  border: 0em;
  border-radius: 8%;
  color: rgb(255, 255, 255);
  font-size: 16px;
  padding: 0.76rem 2.4rem;
}

/* Modal Styles */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background: white;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}


</style>
-->
