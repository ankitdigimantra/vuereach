<template>
  <div class="layout">
    <div class="division">
      <LeftBar class="leftbar" />
      <!-- <LetStart @modeSelected="changeMode" class="rightbar" /> -->
      <component :is="currentComponent" class="rightbar"/>
    </div>
  </div>
</template>
 
<script>
import LeftBar from "./LeftSide/LeftBar.vue";
import LetStart from "./RightSide/LetStart.vue";
import ShipPrefer from "./RightSide/ShipPrefer.vue";
import ReadyAccount from "./RightSide/ReadyAccount.vue";
import EventBus from '@/EventBus';
 
export default {
  name: "LayoutTemp",
  components: {
    LeftBar,
    LetStart,
    ShipPrefer,
    ReadyAccount,
  },
  data() {
    return {
      currentComponent: "LetStart", // Initial component
    };
  },
  methods: {
    changeMode() {
      // Handle mode change if needed
    },
    // Method to handle Next button click from LetStart component
    handleNextClicked() {
      
      this.currentComponent = "ShipPrefer"; // Switch to ShipPrefer component
    },

    handleShipNextClicked() {
      this.currentComponent = "ReadyAccount";
    },
  },
  mounted() {
    // Listen for the event emitted by LetStart component
    // this.$on("nextClicked", this.handleNextClicked);
    // emitter.on("nextClicked", this.handleNextClicked);
    EventBus.on("nextClicked", this.handleNextClicked);
    EventBus.on("shipNextClicked", this.handleShipNextClicked);
    // console.log("sfsdfsdfsdf")
 
  },
};
</script>
 
<style scoped>
html, body, #app {
  height: 100%;
  margin: 0;
  background-color: transparent;
}
 
.division {
  width: 100%;
  display: flex;
  height:100%;
}
 
.leftbar, .rightbar {
  flex: 1;
  min-width: 50%;
}
 
.leftbar {
  background-color: rgb(233, 243, 240);
  display: flex;
  justify-content: center;
  align-items: center;
}
 
.rightbar {
  background-color: rgb(255, 255, 255);
  display: flex;
  justify-content: center;
  align-items: center;
}
 
@media (max-width: 1024px) {
  .division {
    flex-direction: column;
  }
  
  .leftbar, .rightbar {
    min-width: 100%;
  }
}
</style>