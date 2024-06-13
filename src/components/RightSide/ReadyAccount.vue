<template>
  <div class="aligncenter">
    <div class="contain">
      <div class="rightbar">
        <img alt="Vue logo" src="../../assets/rocket.png" height="66" />
        <h1>Your account is ready!</h1>
      </div>
      <!-- < @submit.prevent="proceedToNextPage"> -->

      <p class="para">What's next?</p>
      <div class="form-explore-actions">
        <button
          class="next-button"
          type="submit"
          @click="goToShippingPreferences"
        ><svg height="20" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M0 93.7l183.6-25.3v177.4H0V93.7zm0 324.6l183.6 25.3V268.4H0v149.9zm203.8 28L448 480V268.4H203.8v177.9zm0-380.6v180.1H448V32L203.8 65.7z"/></svg>
          Explore the DashBoard
        </button>
      </div>

      <p class="para">Or, If you have a receipt ready upload it now!</p>

      <div class="form-upload-actions">
        <button
          class="next-button"
          type="submit"
          @click="goToShippingPreferences"
        >
          + Upload your first order
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import EventBus from "@/EventBus";

export default {
  name: "ReadyAccount",

  methods: {
    goToShippingPreferences() {
      EventBus.emit("shipNextClicked");
    },
  },
};
</script>

<style scoped>
h1 {
  color: #2e6666;
  margin: 0;
  padding-bottom: 40px;
}

.aligncenter {
  display: flex;
  flex-direction: column; 
  justify-content: center;
  align-content: center;
  height: 100%;
}

.para {
  color: rgb(143, 143, 143);
  margin-top: 10px;
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  margin-top: 40px;
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
  /* padding: 12px; */
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

.form-explore-actions button {
  padding: 1rem 1rem;
  border: 1px solid#ebebeb;
  border-radius: 4px;
  cursor: pointer;
  color: rgb(0, 0, 0);
  background-color: #f5f5f5;
  width: 100%;
  font-size:medium;
  border: 2px solid#f5f5f5;
  display: flex;
  align-items: center;
  gap: 8px;
  justify-content: center;
}

.form-upload-actions button {
  padding: 1rem 1rem;
  border: 1px solid#ebebeb;
  border-radius: 4px;
  cursor: pointer;
  color: #2e6666;
  background-color: #f5f5f5;
  width: 100%;
  font-size:medium;
  border: 2px solid#f5f5f5;
}


/* background-color: #2e6666; */


.next-button {
  padding: 4px;
}
</style>
