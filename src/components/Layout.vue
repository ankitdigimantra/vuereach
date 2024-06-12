<template>
  <div class="layout">
    <div class="division">
      <LeftBar @modeSelected="changeMode" class="leftbar" />
      <LetStart @modeSelected="changeMode" class="rightbar" />
    </div>
  </div>
</template>

<script>
import LeftBar from "./LeftSide/LeftBar.vue";
import LetStart from "./RightSide/LetStart.vue";

export default {
  name: "LayoutTemp",
  components: {
    LeftBar,
    LetStart
  }
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
