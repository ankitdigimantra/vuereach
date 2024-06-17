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
              <label class="label" for="firstname" style="display: flex;">First Name</label>
              <input
                type="text"
                id="firstname"
                v-model="firstname"
                placeholder="First Name"
                @input="validateName"
                :class="{ 'error-border': !isValidName }"
                required
              />
              <span v-if="!isValidName" class="error-message">Please enter a valid name without spaces</span>
            </div>
            <div class="column">
              <label class="label" for="lastname" style="display: flex;">Last Name</label>
              <input
                type="text"
                id="lastname"
                v-model="lastname"
                placeholder="Last Name"
                @input="validateLastName"
                :class="{ 'error-border': !isValidLastName }"
                required
              />
              <span v-if="!isValidLastName" class="error-message">Please enter a valid name without spaces</span>
            </div>
          </div>
          <label class="label" for="address" style="display: flex;">Billing address</label>
          <input
            type="text"
            id="address"
            v-model="address"
            placeholder="1234 Queen Street"
            @input="validateAddress"
            :class="{ 'error-border': !isValidAddress }"
            required
          />
          <span v-if="!isValidAddress" class="error-message">Please enter a valid address</span>

          <div class="flex">
            <div class="column">
              <label class="label" for="postal" style="display: flex;">Postal Code</label>
              <input
                type="text"
                id="postal"
                v-model="postal"
                placeholder="Postal Code"
                @input="validatePostal"
                :class="{ 'error-border': !isValidPostal }"
                required
              />
              <span v-if="!isValidPostal" class="error-message">Please enter a valid postal code</span>
            </div>
            <div class="column">
              <label class="label" for="province" style="display: flex;">Province</label>
              <select
                id="province"
                v-model="province"
                @change="validateProvince"
                :class="{ 'error-border': !isValidProvince }"
                required
              >
                <option disabled value="">Please select one</option>
                <option v-for="province in provinces" :key="province" :value="province">
                  {{ province }}
                </option>
              </select>
              <span v-if="!isValidProvince" class="error-message">Please select a valid province</span>
            </div>
          </div>

          <label class="label" for="number" style="display: flex;">Phone Number</label>
          <input
            type="text"
            id="number"
            v-model="number"
            placeholder="Phone Number"
            @input="validateNumber"
            :class="{ 'error-border': !isValidNumber }"
            required
          />
          <span v-if="!isValidNumber" class="error-message">Please enter a valid phone number</span>
        </div>
        <div class="form-actions">
          <button
            class="next-button"
            type="submit"
            @click="goToShippingPreferences"
            :disabled="!isFormValid"
          >
            Next
          </button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
import EventBus from "@/EventBus";

export default {
  name: "LetStart",
  data() {
    return {
      firstname: "",
      lastname: "",
      address: "",
      postal: "",
      province: "",
      number: "",
      isValidName: true,
      isValidLastName: true,
      isValidAddress: true,
      isValidPostal: true,
      isValidProvince: true,
      isValidNumber: true,
      provinces: ["Province 1", "Province 2", "Province 3", "Province 4"], // Replace with actual provinces
    };
  },
  computed: {
    isFormValid() {
      return (
        this.isValidName &&
        this.isValidLastName &&
        this.isValidAddress &&
        this.isValidPostal &&
        this.isValidProvince &&
        this.isValidNumber &&
        this.firstname &&
        this.lastname &&
        this.address &&
        this.postal &&
        this.province &&
        this.number
      );
    },
  },
  methods: {
    goToShippingPreferences() {
      EventBus.emit("nextClicked");
    },
    validateName() {
      const namePattern = /^[^\s]+$/;
      this.isValidName = namePattern.test(this.firstname);
    },
    validateLastName() {
      const namePattern = /^[^\s]+$/;
      this.isValidLastName = namePattern.test(this.lastname);
    },
    validateAddress() {
      this.isValidAddress = this.address.trim().length > 0;
    },
    validatePostal() {
      const postalPattern = /^[A-Za-z0-9\s]+$/;
      this.isValidPostal = postalPattern.test(this.postal);
    },
    validateProvince() {
      this.isValidProvince = this.province.trim().length > 0;
    },
    validateNumber() {
      const numberPattern = /^[0-9]+$/;
      this.isValidNumber = numberPattern.test(this.number);
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

select {
  background-color: #FFF;
}

input.error-border,
select.error-border {
  border: 1px solid red !important;
}

input:focus,
select:focus {
  outline: none;
}

.error-message {
  color: red;
  font-size: 12px;
  margin-top: 1px;
  display: flex;
  justify-content: flex-start;
}

.aligncenter {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  height: 100%;
}

.para {
  color: rgb(143, 143, 143);
  margin-top: 10px;
  margin-bottom: 60px;
}

.contain {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 10px;
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
  width: 48%;
  display: flex;
  flex-direction: column;
}

.label {
  margin-bottom: 8px;
  font-size: 16px;
  padding: 20px 0 0 0;
}

input,
select {
  padding: 12px;
  font-size: 16px;
  margin-bottom: 1px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
  box-sizing: border-box;
}

form {
  padding: 10px;
}

.form-group {
  margin-bottom: 1rem;
  gap: 20px;
  justify-content: flex-start;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
}

.form-group input,
.form-group select {
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

.form-actions button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

.next-button {
  padding: 4px;
  font-size: 16px;
}
</style>
