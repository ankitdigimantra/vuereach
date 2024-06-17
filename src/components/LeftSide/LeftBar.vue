<template>
  <div class="sidebar">
    <div class="contain">
      <img alt="Vue logo" src="../../assets/truck.png" height="86" />
    </div>
    <div class="progressbar">
      <h1 class="head">
        Welcome to
        <br />Reach!
      </h1>
    </div>
    <div class="flex">
     <HorizontalPB :activeStep="activeStep" :steps="steps" />
    <VerticalPB :activeStep="activeStep" :steps="steps" />
  </div>
  </div>
</template>
 
<script>
import EventBus from "@/EventBus";
import VerticalPB from "./VerticalPB.vue";
import HorizontalPB from "./HorizontalPB.vue";
 
export default {
  name: "LeftBar",
  components: {
    VerticalPB,
    HorizontalPB,
  },
  data() {
    return {
      activeStep: "start",
      steps: ["start", "progress", "account"],
    };
  },
  methods: {
    handleNextClicked() {
      const currentStepIndex = this.steps.indexOf(this.activeStep);
      if (currentStepIndex < this.steps.length - 1) {
        this.activeStep = this.steps[currentStepIndex + 1];
      }
    },
    handleBackClicked() {
      this.activeStep = "start";
    },
  },
  mounted() {
    EventBus.on("nextClicked", this.handleNextClicked);
    EventBus.on("shipNextClicked", this.handleNextClicked);
    EventBus.on("backClicked", this.handleBackClicked);
  },
  beforeUnmount() {
    EventBus.off("nextClicked", this.handleNextClicked);
    EventBus.off("shipNextClicked", this.handleNextClicked);
    EventBus.off("backClicked", this.handleBackClicked);
  },
};
</script>
 
<style scoped>
h1 {
  color: #000000;
  font-size: xxx-large;
  text-align: start;
}
 
.flex{
  display:flex;
  justify-content: center;
}
.sidebar {
  width: 100%;
 
  flex-direction: column;
}
 
.contain {
  margin-bottom: 100px;
}
 
@media (max-width: 1024px) {
.sidebar {
  max-height: 415px;
}

  .contain {
    margin-bottom: 10px;
  }
 
  .progressbar {
    margin-bottom: 2px;
  }
 
  .progressbar-content {
    display: none !important;
  }
}
 
.progressbar {
  margin-bottom: 20px;
}
</style>