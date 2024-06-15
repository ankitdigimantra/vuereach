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
    <VerticalPB class="" />
    <div class="progressbar-content">
      <!-- First Step -->
      <div class="step-container">
        <div
          class="progress-indicator-circle"
          :class="{
            greenBackground: isActiveStep('progress') || isCompletedStep('progress'),
          }"
        >
        <img
            v-if="isActiveStep('progress') || isCompletedStep('progress')"
            alt="Tick logo"
            src="../../assets/White_check.svg.png"
            class="tick-logo"
          />
          <div
            class="progress-inside-indicator-circle"
            :class="{
              greenBackground: isActiveStep('start') || isCompletedStep('start'),
            }"
          ></div>
        </div>

        <div
          class="progress-indicator"
          :class="{
            greenBackground: isActiveStep('start') || isCompletedStep('start'),
          }"
        ></div>
        <div
          class="step"
          :class="{
            textColorActive: isActiveStep('start'),
            textColorCompleted: isCompletedStep('start'),
          }"
        >
          <p>Let's get started</p>
        </div>
      </div>

      <!-- Second Step -->
      <div class="step-container">
        <div
          class="progress-indicator-circle-two"
          :class="{
            greenBorder: isActiveStep('progress') || isCompletedStep('progress'),
            greenBackground: isActiveStep('account') || isCompletedStep('account')
          }"
        >
        <img
            v-if="isActiveStep('account') || isCompletedStep('account')"
            alt="Tick logo"
            src="../../assets/White_check.svg.png"
            class="tick-logo-two"
          />
          <div
            class="progress-inside-indicator-circle-two"
            :class="{
              greenBackground: isActiveStep('progress') || isCompletedStep('progress') || isActiveStep('account') || isCompletedStep('account'),
            }"
          ></div>
        </div>
        <div
          class="progress-indicator-two"
          :class="{
            greenBackground: isActiveStep('progress') || isCompletedStep('progress'),
          }"
        ></div>
        <div
          class="step"
          :class="{
            textColorActive: isActiveStep('progress'),
            textColorCompleted: isCompletedStep('progress'),
          }"
        >
          <p>Shipping Preferences</p>
        </div>
      </div>

      <!-- Third Step -->
      <div class="step-container">
        <div
          class="progress-indicator-circle-three"
          :class="{
            greenBackground: isActiveStep('account') || isCompletedStep('account'),
          }"
        >
        <img
            v-if="isActiveStep('account') || isCompletedStep('account')"
            alt="Tick logo"
            src="../../assets/White_check.svg.png"
            class="tick-logo-two"
          />
          <div
            class="progress-inside-indicator-circle-three"
            :class="{
              greenBackground: isActiveStep('account') || isCompletedStep('account'),
            }"
          ></div>
        </div>
        <div
          class="step"
          :class="{
            textColorActive: isActiveStep('account'),
            textColorCompleted: isCompletedStep('account'),
          }"
        >
          <p>Your Account is ready</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import EventBus from "@/EventBus";
// import VerticalPB from "./ProgressIndicator.vue"

export default {
  name: "LeftBar",
  components: {
    // VerticalPB
  },
  data() {
    return {
      activeStep: "start",
      steps: ["start", "progress", "account"],
    };
  },
  methods: {
    isActiveStep(step) {
      return this.activeStep === step;
    },
    isCompletedStep(step) {
      const currentStepIndex = this.steps.indexOf(this.activeStep);
      const stepIndex = this.steps.indexOf(step);
      return stepIndex < currentStepIndex;
    },
    handleNextClicked() {
      const currentStepIndex = this.steps.indexOf(this.activeStep);
      if (currentStepIndex < this.steps.length - 1) {
        this.activeStep = this.steps[currentStepIndex + 1];
      }
    },
  },
  mounted() {
    EventBus.on("nextClicked", this.handleNextClicked);
    EventBus.on("shipNextClicked", this.handleNextClicked);
  },
};
</script>

<style scoped>
h1 {
  color: #000000;
  font-size: xxx-large;
  text-align: start;
}

p {
  color: #818181;
  margin: 30px;
}

.textColorActive p {
  color: #000000;
}

.textColorCompleted p {
  color: #000000;
}

.greenBackground {
  background-color: #2e6666;
  z-index: 2;
}

.line {
  background-color: #2e6666;
  z-index: 2;
}

.greenBorder {
  border-color: #2e6666;
}

.sidebar {
  width: 100%;
  display: flex;
  flex-direction: column;
}

.contain {
  margin-bottom: 100px;
}

@media (max-width: 1024px) {
  .contain {
  margin-bottom: 10px;
}

.progressbar {
  margin-bottom: 2px;
}

.progressbar-content{
  display: none !important;
}

}


.progressbar {
  margin-bottom: 20px;
}

.progressbar-content {
  margin-bottom: 40px;
  align-items: flex-start;
  display: flex;
  flex-direction: column;
  position: relative;
}

.step-container {
  display: flex;
  align-items: center;
  margin-left: 20px;
  height: 80px;
}

.progress-inside-indicator-circle {
  width: 10px;
  height: 10px;
  border: 3px solid #2e6666;
  border-radius: 50%;
  padding: 1px;
  position: absolute;
  top: 12px;
  left: 10px;
}

.progress-inside-indicator-circle-two {
  width: 14px;
  height: 14px;
  background-color: #919191;
  border-radius: 50%;
  padding: 1px;
  position: absolute;
  top: 12px;
  left: 12px;
  z-index: 1;
}

.progress-inside-indicator-circle-three {
  width: 14px;
  height: 14px;
  /* border: 3px solid #919191; */
  background-color: #919191;
  border-radius: 50%;
  padding: 1px;
  position: absolute;
  top: 12px;
  left: 12px;
}

.progress-indicator-circle {
  width: 18px;
  height: 20px;
  margin-right: 10px;
  border: 3px solid #2e6666;
  border-radius: 50%;
  padding: 10px;
  position: absolute;
  top: 18px;
  left: -8px;
}

.progress-indicator-circle-two {
  width: 18px;
  height: 20px;
  z-index: 10;
  margin-right: 10px;
  border: 3px solid #919191;
  border-radius: 50%;
  padding: 10px;
  position: absolute;
  top: 96px;
  left: -7px;
}

.progress-indicator-circle-three {
  width: 18px;
  height: 20px;
  margin-right: 10px;
  border: 3px solid #919191;
  border-radius: 50%;
  padding: 10px;
  position: absolute;
  top: 176px;
  left: -7px;
}

.progress-indicator {
  width: 3px;
  height: 34px;
  margin-right: 10px;
  position: absolute;
  top: 62px;
  left: 13px;
}

.progress-indicator-two {
  width: 3px;
  height: 35px;
  z-index: 1;
  background-color: #919191;
  margin-right: 10px;
  position: absolute;
  top: 141px;
  left: 13px;
}

.progress-indicator-two.greenBackground {
  background-color: #2e6666;
}

.progress-indicator-circle-two.greenBackground {
  border: 3px solid #2e6666;
}

.progress-inside-indicator-circle-two.greenBackground {
  background-color: #2e6666;
  
}

.progress-indicator-circle-two.greenBorder {
  border: 3px solid #2e6666;
  /* background-color: #2e6666; */

}
.progress-indicator-circle-three.greenBackground {
  border: 3px solid #2e6666;
  /* background-color: #2e6666; */

}

.progress-inside-indicator-circle-three.greenBackground {
  background-color: #2e6666;
}



.step {
  position: relative;
}

.tick-logo {
  position: absolute;
  top: 12px;
  left: 10px;
  width: 20px;
  height: 16px;
  z-index: 11;
}

.tick-logo-two {
  position: absolute;
  top: 12px;
  left: 10px;
  width: 20px;
  height: 16px;
  z-index: 11;
}

.tick-logo-three {
  position: absolute;
  top: 12px;
  left: 10px;
  width: 20px;
  height: 16px;
  z-index: 11;
}
</style>
