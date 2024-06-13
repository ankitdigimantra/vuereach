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
    <div class="content">
      <div class="step-container">
        <div class="progress-indicator-circle" :class="{
          greenBackground:
            isActiveStep('progress') || isCompletedStep('progress'),
        }">
          <div class="progress-inside-indicator-circle" :class="{
            greenBackground:
              isActiveStep('start') || isCompletedStep('start'),
          }"></div>
        </div>

        <div class="progress-indicator" :class="{
          greenBackground: isActiveStep('start') || isCompletedStep('start'),
        }"></div>
        <div class="step" :class="{
          textColorActive: isActiveStep('start'),
          textColorCompleted: isCompletedStep('start'),
        }">
          <p>Let's get started</p>
        </div>
      </div>
      <!-- //progresss baar start from herer -->
      <div class="step-container">
        <div class="progress-indicator-circle-two" :class="{
          greenBackground:
            isActiveStep('account') || isCompletedStep('account'),
        }">
          <div class="progress-inside-indicator-circle-two" :class="{
            greenBackground:
              isActiveStep('progress') || isCompletedStep('progress'),
          }"></div>
        </div>

        <div class="progress-indicator-two" :class="{
          greenBackground:
            isActiveStep('progress') || isCompletedStep('progress'),
        }"></div>
        <div class="step" :class="{
          textColorActive: isActiveStep('progress'),
          textColorCompleted: isCompletedStep('progress'),
        }">
          <p>Shipping Preferences</p>
        </div>
      </div>

      <!-- /account ready start from herer -->
      <div class="step-container">
        <div class="progress-indicator-circle-three" :class="{ greenBac }">
          <div class="progress-inside-indicator-circle-three" :class="{
            greenBackground:
              isActiveStep('account') || isCompletedStep('account'),
          }"></div>
        </div>

        <!-- <div class="progress-indicator" :class="{ greenBackground: isActiveStep('account') || isCompletedStep('account') }"></div> -->
        <div class="step" :class="{
          textColorActive: isActiveStep('account'),
          textColorCompleted: isCompletedStep('account'),
        }">
          <p>Your Account is ready</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import EventBus from "@/EventBus";

export default {
  name: "LeftBar",
  data() {
    return {
      activeStep: "start",
      steps: ["start", "progress", "account"]
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
    }
  },
  mounted() {
    EventBus.on("nextClicked", this.handleNextClicked);
    EventBus.on("shipNextClicked", this.handleNextClicked);
  }
};
</script>

<style scoped>
h1 {
  color: #000000;
  font-size: xxx-large;
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
}

.greenBorder {
  background-color: #2e6666;
}

.sidebar {
  width: 100%;
  display: flex;
  flex-direction: column;
}

.contain {
  margin-bottom: 140px;
}

.progressbar {
  margin-bottom: 20px;
}

.content {
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
  /* Adjust the height as needed */
}

.progress-inside-indicator-circle {
  width: 10px;
  height: 10px;
  /* Adjust to match the step-container height */
  /* margin-right: 10px; */
  border: 3px solid #2e6666;
  border-radius: 50%;
  padding: 1px;
  position: absolute;
  top: 12px;
  left: 10px;
}

.progress-inside-indicator-circle-two {
  width: 10px;
  height: 10px;
  /* Adjust to match the step-container height */
  /* margin-right: 10px; */
  border: 3px solid #919191;
  background-color: #919191;
  border-radius: 50%;
  padding: 1px;
  position: absolute;
  top: 12px;
  left: 10px;
}

.progress-inside-indicator-circle-three {
  width: 10px;
  height: 10px;
  /* Adjust to match the step-container height */
  /* margin-right: 10px; */
  border: 3px solid #919191;
  background-color: #919191;
  border-radius: 50%;
  padding: 1px;
  position: absolute;
  top: 12px;
  left: 10px;
}

.progress-indicator-circle {
  width: 18px;
  height: 20px;
  /* Adjust to match the step-container height */
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
  /* Adjust to match the step-container height */
  margin-right: 10px;
  border: 3px solid #919191;
  border-radius: 50%;
  padding: 10px;
  position: absolute;
  top: 96px;
  left: -8px;
}

.progress-indicator-circle-three {
  width: 18px;
  height: 20px;
  /* Adjust to match the step-container height */
  margin-right: 10px;
  border: 3px solid #919191;
  border-radius: 50%;
  padding: 10px;
  position: absolute;
  top: 176px;
  left: -8px;
}

.progress-indicator {
  width: 3px;
  height: 34px;
  /* Adjust to match the step-container height */
  margin-right: 10px;
  position: absolute;
  top: 62px;
  left: 13px;
}

.progress-indicator-two {
  width: 3px;
  height: 34px;
  /* Adjust to match the step-container height */
  margin-right: 10px;
  position: absolute;
  top: 142px;
  left: 13px;
}

.step {
  position: relative;
}
</style>
