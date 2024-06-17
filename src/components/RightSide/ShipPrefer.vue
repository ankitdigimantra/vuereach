<template>
  <div class="contain">
    <div class="container">
      <div class="rightbar">
        <img alt="Vue logo" src="../../assets/truck.png" height="66" />
        <h1>Shipping Preferences</h1>
        <p class="para">Choose your preferred shipping method</p>
      </div>
      <div class="group-switch">
        <div
          class="switch-button switch-l-button"
          :class="{ active: selectedMode === 'pickup' }"
          @click="selectMode('pickup')"
        >
          Pickup in-store
        </div>
        <div
          class="switch-button switch-r-button"
          :class="{ active: selectedMode === 'deliver' }"
          @click="selectMode('deliver')"
        >
          Deliver to home
        </div>
      </div>
      <div class="pickupwidth" v-if="selectedMode === 'pickup'">
        <p class="para" for="country" style="display: flex">Choose a Country</p>
        <select
          class="select-box"
          id="country"
          v-model="selectedCountry"
          required
        >
          <option disabled value="">Please select one</option>
          <option v-for="country in countries" :key="country" :value="country">
            {{ country }}
          </option>
        </select>

        <p class="para" for="city" style="display: flex">Choose a City</p>
        <div style="gap-2" class="selected-city">
          <label
            class="form-explore-actions"
            :class="{ selected: selectedOption === 'missianguaua' }"
          >
            <input
              type="radio"
              id="missianguaua"
              value="missianguaua"
              v-model="selectedOption"
            />
            <div class="flex-off">
              <p>Missianguaua</p>
              <p class="p-gray">Toronto ONCX 2ZX</p>
            </div>
          </label>

          <label
            class="form-explore-actions"
            :class="{ selected: selectedOption === 'toronto' }"
          >
            <input
              type="radio"
              id="toronto"
              value="toronto"
              v-model="selectedOption"
            />
            <div class="flex-off">
              <p>Toronto</p>
              <p class="p-gray">Toronto ONM5V 3L9</p>
            </div>
          </label>

          <label
            class="form-explore-actions"
            :class="{ selected: selectedOption === 'vancouver' }"
          >
            <input
              type="radio"
              id="vancouver"
              value="vancouver"
              v-model="selectedOption"
            />
            <div class="flex-off">
              <p>Vancouver</p>
              <p class="p-gray">Vancouver BCV5K 0A1</p>
            </div>
          </label>
        </div>
      </div>
      <div v-if="selectedMode === 'deliver'" class="deliver-class">
        <label class="form-explore-actions">
          <label class="switch">
            <input type="checkbox" @click="toggleCheckbox" />
            <div class="slider round"></div>
          </label>
          <div class="flex-off">
            <p>Same as bill</p>
          </div>
        </label>

        <form @submit.prevent="proceedToNextPage">
          <div class="form-group">
            <label class="labell" for="email">Home Address</label>
            <input
              class="input-form"
              type="text"
              id="firstname"
              v-model="firstname"
              placeholder="Home Address"
              required
            />

            <div class="form-flex">
              <div class="form-column">
                <label class="labell" for="city">City</label>
                <input
                  class="input-form"
                  type="text"
                  id="city"
                  v-model="city"
                  placeholder="City"
                  required
                />
              </div>

              <div class="form-column">
                <label class="labell" for="postal">Postal Code</label>
                <input
                  class="input-form"
                  type="text"
                  id="postal"
                  v-model="postal"
                  placeholder="Postal Code"
                  required
                />
              </div>
            </div>

            <label class="labell" for="province">Province</label>
            <input
              class="input-form"
              type="text"
              id="province"
              v-model="province"
              placeholder="Province"
              required
            />

            <label class="labell" for="country">Country</label>
            <input
              class="input-form"
              type="text"
              id="country"
              v-model="country"
              placeholder="Country"
              required
            />
          </div>
        </form>
      </div>

      <div class="flex-button">
        <div class="form-column">
          <div class="form-back-actions">
            <button class="next-button" type="button" @click="goToLetsStart">
              Back
            </button>
          </div>
        </div>
        <div class="form-column">
          <div class="form-next-actions">
            <button
              class="next-button"
              type="button"
              :disabled="!isFormValid"
              @click="goToReadyAccount"
            >
              Next
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import EventBus from "@/EventBus";

export default {
  name: "ShipPrefer",
  data() {
    return {
      selectedMode: "pickup",
      selectedCountry: "",
      selectedOption: "",
      countries: [
        "Canada",
        "United States",
        "Mexico",
        "United Kingdom",
        "Germany",
        "France",
        "Australia",
        "India",
      ],
      firstname: "",
      city: "",
      postal: "",
      province: "",
      country: "",
    };
  },
  computed: {
    isFormValid() {
      if (this.selectedMode === "pickup") {
        return this.selectedCountry !== "" && this.selectedOption !== "";
      } else if (this.selectedMode === "deliver") {
        return (
          this.firstname !== "" &&
          this.city !== "" &&
          this.postal !== "" &&
          this.province !== "" &&
          this.country !== ""
        );
      }
      return false;
    },
  },
  methods: {
    goToReadyAccount() {
      EventBus.emit("shipNextClicked");
    },
    goToLetsStart() {
      EventBus.emit("letsStartBackClicked");
    },
    selectMode(mode) {
      this.selectedMode = mode;
    },
    toggleCheckbox() {},
    proceedToNextPage() {},
  },
};
</script>
<style scoped>
h1 {
  color: #2e6666;
  margin: 0;
  padding: 0;
}

p {
  margin: 0;
  padding: 0;
  display: flex;
  align-items: flex-start;
}

.para {
  color: rgb(59, 59, 59);
  margin-top: 10px;
  display: flex;
  align-items: flex-start;
  justify-content: start;
}

label {
  display: flex;
  justify-content: center;
  align-items: center;
}

.labell {
  margin-bottom: 8px;
  font-size: 16px;
  display: flex;
  padding: 6px 0 0 0;

  justify-content: flex-start;
}

.input-form {
  padding: 12px;
  font-size: 16px;
  /* margin-bottom: 16px; */
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
  box-sizing: border-box;
}

.flex {
  display: flex;
  justify-content: space-between;
}
.flex-button {
  /* max-width: 80%; */
  margin: 40px 0 0 0;
  gap: 10px;
  width: 100%;
  display: flex;
  align-content: center;
}

.form-flex {
  display: flex;
  justify-content: space-between;
}

.form-column {
  width: 48%; /* Adjust the width as needed */
  display: flex;
  flex-direction: column;
}

.contain {
  /* width: 320px; */
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.container {
  max-width: 480px;
}

.p-gray {
  color: #727272;
  font-size: 14px;
  text-decoration: underline;
}

select {
  padding: 10px;
  display: flex;
  justify-content: center;
  width: 300px;
  border-radius: 8px;
  font-size: 16px;
  background-color: #ffffff;
  margin: 20px 0 20px 0;
}

.deliver-class {
  max-width: 400px;
}

.select-box {
  width: 100%;
}

.flex {
  display: flex;
  justify-content: space-between;
  margin: 20px 0 0 0;
}

/* .flex-off {
  display: flex;
  flex-direction: column;
} */

.column {
  /* width: 200px; */
  display: flex;
  flex-direction: column;
  gap: 20px;
}

@media (max-width: 1024px) {
  .division {
    flex-direction: row;
  }
  .column {
    width: 100%;
    display: flex;
    flex-direction: row;
  }

  select {
    /* width: 280px; */
    display: flex;
    justify-content: center;
  }

  .group-switch {
    padding: 0px !important;
    /* margin: 10px 0 10px 0; */
    margin: 30px 0 30px 0 !important;
  }
}

.rightbar {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.selected-city {
  gap: 2;
  margin: 10px 0 10px 0;
  width: 400px;
}

@media (max-width: 786px) {
  .selected-city {
    max-width: 360px;
  }
 
  .switch-button {
    padding: 10px;
    margin-top: 2px;
  }
   
}


@media (max-width: 375px) {
  .selected-city {
    max-width: 280px;
  }
 
  .switch-button {
    padding: 10px;
    margin-top: 2px;
  }
   
}
/* @media (max-width: 1024px) {
  .selected-city {
    max-width: 360px;
  }
} */

.switch-button {
  padding: 14px;
  margin-top: 20px;
  cursor: pointer;
  transition: background-color 0.3s, color 0.3s;
  border: 1px solid #ebebeb;
}

.switch-r-button {
  background-color: #ffffff;
  color: black;
  border-radius: 0 8px 8px 0;
}

.switch-l-button {
  background-color: #ffffff;
  color: black;
  border-radius: 8px 0 0 8px;
}

.switch-button.active {
  background-color: #2e6666;
  color: white;
}

.group-switch {
  display: flex;
  justify-content: center;
  padding: 0 30px;
  margin: 40px 0 40px 0;
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
  border-radius: 8px;
  cursor: pointer;
  color: white;
  background-color: #2e6666;
  width: 100%;
}

.form-back-actions button {
  padding: 0.6rem 0.6rem;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  color: rgb(0, 0, 0);
  background-color: #f5f5f5;
  width: 100%;
  font-size: medium;
  border: 2px solid #f5f5f5;
  display: flex;
  align-items: center;
  gap: 8px;
  justify-content: center;
}

.form-next-actions button {
  padding: 0.6rem 0.6rem;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  color: #ffffff;
  background-color: #2e6666;
  width: 100%;
  font-size: medium;
  border: 2px solid #f5f5f5;
}

.form-explore-actions {
  padding: 1rem 1rem;
  margin: 10px 0 10px 0;
  border-radius: 4px;
  cursor: pointer;
  color: rgb(0, 0, 0);
  background-color: #ffffff;
  font-size: medium;
  border: 2px solid #f5f5f5;
  display: flex;
  align-items: center;
  gap: 8px;
  justify-content: flex-start;
  border: 1px solid #ebebeb;
}

.form-explore-actions.selected {
  background-color: #f3f3f3;
  border: 1px solid#2e6666;
}

.next-button {
  padding: 4px;
}

/* //fpr the toogle button */
.switch {
  position: relative;
  display: inline-block;
  width: 32px;
  height: 18px;
}

.switch input {
  display: none;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 14px;
  width: 14px;
  left: 2px;
  bottom: 2px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #2e6666;
}

input:focus + .slider {
  box-shadow: 0 0 1px #e0e0e0;
}

input:checked + .slider:before {
  -webkit-transform: translateX(14px);
  -ms-transform: translateX(14px);
  transform: translateX(14px);
}

.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>

<!--<template>
  <div class="contain">
    <div class="container">
      <div class="rightbar">
        <img alt="Vue logo" src="../../assets/truck.png" height="66" />
        <h1>Shipping Preferences</h1>
        <p class="para">Choose your preferred shipping method</p>
      </div>
      <div class="group-switch">
        <div
          class="switch-button switch-l-button"
          :class="{ active: selectedMode === 'pickup' }"
          @click="selectMode('pickup')"
        >
          Pickup in-store
        </div>
        <div
          class="switch-button switch-r-button"
          :class="{ active: selectedMode === 'deliver' }"
          @click="selectMode('deliver')"
        >
          Deliver to home
        </div>
      </div>
      <div class="pickupwidth" v-if="selectedMode === 'pickup'">
        <p class="para" for="country" style="display: flex">Choose a Country</p>
        <select
          class="select-box"
          id="country"
          v-model="selectedCountry"
          required
        >
          <option disabled value="">Please select one</option>
          <option v-for="country in countries" :key="country" :value="country">
            {{ country }}
          </option>
        </select>

        <p class="para" for="city" style="display: flex">Choose a City</p>
        <div style="gap-2" class="selected-city">
          <label
            class="form-explore-actions"
            :class="{ selected: selectedOption === 'missianguaua' }"
          >
            <input
              type="radio"
              id="missianguaua"
              value="missianguaua"
              v-model="selectedOption"
            />
            <div class="flex-off">
              <p>Missianguaua</p>
              <p class="p-gray">Toronto ONCX 2ZX</p>
            </div>
          </label>

          <label
            class="form-explore-actions"
            :class="{ selected: selectedOption === 'toronto' }"
          >
            <input
              type="radio"
              id="toronto"
              value="toronto"
              v-model="selectedOption"
            />
            <div class="flex-off">
              <p>Toronto</p>
              <p class="p-gray">Toronto ONM5V 3L9</p>
            </div>
          </label>

          <label
            class="form-explore-actions"
            :class="{ selected: selectedOption === 'vancouver' }"
          >
            <input
              type="radio"
              id="vancouver"
              value="vancouver"
              v-model="selectedOption"
            />
            <div class="flex-off">
              <p>Vancouver</p>
              <p class="p-gray">Vancouver BCV5K 0A1</p>
            </div>
          </label>
        </div>
      </div>
      <div v-if="selectedMode === 'deliver'" class="deliver-class">
        <label class="form-explore-actions">
          <label class="switch">
            <input type="checkbox" @click="toggleCheckbox" />
            <div class="slider round"></div>
          </label>
          <div class="flex-off">
            <p>Same as bill</p>
          </div>
        </label>

        <form @submit.prevent="proceedToNextPage">
          <div class="form-group">
            <label class="labell" for="email">Home Address</label>
            <input
              class="input-form"
              type="name"
              id="firstname"
              v-model="firstname"
              placeholder="Home Address"
              required
            />

            <div class="form-flex">
              <div class="form-column">
                <label class="labell" for="email">City</label>
                <input
                  class="input-form"
                  type="address"
                  id="address"
                  v-model="address"
                  placeholder="City"
                  required
                />
              </div>

              <div class="form-column">
                <label class="labell" for="email">Postal Code</label>
                <input
                  class="input-form"
                  type="postal"
                  id="postal"
                  v-model="postal"
                  placeholder="Postal Code"
                  required
                />
              </div>
            </div>

            <label class="labell" for="password">Province</label>
            <input
              class="input-form"
              type="province"
              id="province"
              v-model="province"
              placeholder="Province"
              required
            />

            <label class="labell" for="password">Country</label>
            <input
              class="input-form"
              type="phonenumber"
              id="number"
              v-model="number"
              placeholder="Country"
              required
            />
          </div>
        </form>
      </div>

      <div class="flex-button">
        <div class="form-column">
          <div class="form-back-actions">
            <button
              class="next-button"
              type="submit"
              @click="goToLetsStart"
            >
              Back
            </button>
          </div>
        </div>
        <div class="form-column">
          <div class="form-next-actions">
            <button class="next-button" type="submit" @click="goToReadyAccount">
              Next
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import EventBus from "@/EventBus";

export default {
  name: "ShipPrefer",
  data() {
    return {
      selectedMode: "pickup",
      selectedCountry: "",
      selectedOption: "",
      countries: [
        "Canada",
        "United States",
        "Mexico",
        "United Kingdom",
        "Germany",
        "France",
        "Australia",
        "India",
      ],
    };
  },
  methods: {
    goToReadyAccount() {
      EventBus.emit("shipNextClicked");
    },
    goToLetsStart() {
      EventBus.emit("letsStartBackClicked");
    },
    
    selectMode(mode) {
      this.selectedMode = mode;
    },
  },
};
</script>

<style scoped>
h1 {
  color: #2e6666;
  margin: 0;
  padding: 0;
}

p {
  margin: 0;
  padding: 0;
  display: flex;
  align-items: flex-start;
}

.para {
  color: rgb(59, 59, 59);
  margin-top: 10px;
  display: flex;
  align-items: flex-start;
  justify-content: start;
}

label {
  display: flex;
  justify-content: center;
  align-items: center;
}

.labell {
  margin-bottom: 8px;
  font-size: 16px;
  display: flex;
  padding: 6px 0 0 0;
  
  justify-content: flex-start;
}

.input-form {
  padding: 12px;
  font-size: 16px;
  /* margin-bottom: 16px; */
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
  box-sizing: border-box;
}

.flex {
  display: flex;
  justify-content: space-between;
}
.flex-button {
  /* max-width: 80%; */
  margin: 40px 0 0 0 ;
  gap: 10px;
  width: 100%;
  display: flex;
  align-content: center;
}

.form-flex {
  display: flex;
  justify-content: space-between;
}

.form-column {
  width: 48%; /* Adjust the width as needed */
  display: flex;
  flex-direction: column;
}

.contain {
  /* width: 320px; */
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.container{
  max-width: 480px;
}

.p-gray {
  color: #727272;
  font-size: 14px;
}

select {
  padding: 10px;
  display: flex;
  justify-content: center;
  width: 300px;
  border-radius: 8px;
  font-size: 16px;
  background-color: #ffffff;
  margin: 20px 0 20px 0;
}

.deliver-class {
  max-width: 400px;
}

.select-box {
  width: 100%;
}

.flex {
  display: flex;
  justify-content: space-between;
  margin: 20px 0 0 0;
}

/* .flex-off {
  display: flex;
  flex-direction: column;
} */

.column {
  /* width: 200px; */
  display: flex;
  flex-direction: column;
  gap: 20px;
}

@media (max-width: 1024px) {
  .division {
    flex-direction: row;
  }
  .column {
    width: 100%;
    display: flex;
    flex-direction: row;
  }

  select {
    /* width: 280px; */
    display: flex;
    justify-content: center;
  }
}

.rightbar {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.selected-city {
  gap: 2;
  margin: 10px 0 10px 0;
  width: 400px;
}

@media (max-width: 786px) {
  .selected-city {
    max-width: 280px;
  }
}

/* @media (max-width: 1024px) {
  .selected-city {
    max-width: 360px;
  }
} */

.switch-button {
  padding: 14px;
  margin-top: 20px;
  cursor: pointer;
  transition: background-color 0.3s, color 0.3s;
  border: 1px solid #ebebeb;
}

.switch-r-button {
  background-color: #ffffff;
  color: black;
  border-radius: 0 8px 8px 0;
}

.switch-l-button {
  background-color: #ffffff;
  color: black;
  border-radius: 8px 0 0 8px;
}

.switch-button.active {
  background-color: #2e6666;
  color: white;
}

.group-switch {
  display: flex;
  padding: 0 30px;
  margin: 40px 0 40px 0;
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
  border-radius: 8px;
  cursor: pointer;
  color: white;
  background-color: #2e6666;
  width: 100%;
}

.form-back-actions button {
  padding: 0.6rem 0.6rem;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  color: rgb(0, 0, 0);
  background-color: #f5f5f5;
  width: 100%;
  font-size: medium;
  border: 2px solid #f5f5f5;
  display: flex;
  align-items: center;
  gap: 8px;
  justify-content: center;
}

.form-next-actions button {
  padding: 0.6rem 0.6rem;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  color: #ffffff;
  background-color: #2e6666;
  width: 100%;
  font-size: medium;
  border: 2px solid #f5f5f5;
}

.form-explore-actions {
  padding: 1rem 1rem;
  margin: 10px 0 10px 0;
  border-radius: 4px;
  cursor: pointer;
  color: rgb(0, 0, 0);
  background-color: #ffffff;
  font-size: medium;
  border: 2px solid #f5f5f5;
  display: flex;
  align-items: center;
  gap: 8px;
  justify-content: flex-start;
  border: 1px solid #ebebeb;
}

.form-explore-actions.selected {
  background-color: #f3f3f3;
  border: 1px solid#2e6666;
}

.next-button {
  padding: 4px;
}

/* //fpr the toogle button */
.switch {
  position: relative;
  display: inline-block;
  width: 32px;
  height: 18px;
}

.switch input {
  display: none;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 14px;
  width: 14px;
  left: 2px;
  bottom: 2px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #008cff;
}

input:focus + .slider {
  box-shadow: 0 0 1px #e0e0e0;
}

input:checked + .slider:before {
  -webkit-transform: translateX(14px);
  -ms-transform: translateX(14px);
  transform: translateX(14px);
}

.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style> -->
