<template>
  <div class="contain">
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
  </div>
</template>

<script>
export default {
  name: "ShipPrefer",
  data() {
    return {
      selectedMode : 'pickup',
    };
  },
  methods: {
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

.para {
  color: rgb(143, 143, 143);
  margin-top: 10px;
}

.contain {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0 80px 0 160px;
}

.rightbar {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 100%;
}

.switch-button {
  padding: 18px;
  margin-top: 20px;
  cursor: pointer;
  transition: background-color 0.3s, color 0.3s;
  border: 1px solid#ebebeb;
}

.switch-r-button {
  background-color: #ffffff;
  color: black;
  border-radius: 0 4px 4px 0;
}

.switch-l-button {
  background-color: #ffffff;
  color: black;
  border-radius: 4px 0 0 4px;
}

.switch-button.active {
  background-color: #2e6666;
  color: white;
}


.group-switch {
  display: flex;
  padding: 0 30px;
}
</style>
