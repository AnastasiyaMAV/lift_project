<template>
  <div class="app">
    <lift-shaft-component
      :valueLevel="valueLevel"
      :upwardMovement="upwardMovement"
      :downwardMovement="downwardMovement"
    />
    <floor-component 
      :levels="levels"
      :upwardMovement="upwardMovement"
      :downwardMovement="downwardMovement"
      :valueLevel="valueLevel"
      @movement="elevatorMovement" />
    <div class="btnGroup">
      <main-button @click="clearLocalStorage">Сбросить</main-button>
    </div>
  </div>
</template>

<script>
import FloorComponent from "./components/FloorComponent.vue";
import LiftShaftComponent from "./components/LiftShaftComponent.vue";

export default {
  components: { LiftShaftComponent, FloorComponent },
  data() {
    return {
      levels: [
        { id: 5, title: "5" },
        { id: 4, title: "4" },
        { id: 3, title: "3" },
        { id: 2, title: "2" },
        { id: 1, title: "1" },
      ],
      valueLevel: localStorage.getItem("level") || "1",
      valueLevelPred: 1,
      upwardMovement: false,
      downwardMovement: false,
    };
  },

  methods: {
    elevatorMovement(value) {
      this.valueLevelPred = this.valueLevel;
      this.valueLevel = value;
      localStorage.setItem("level", value);
      if (this.valueLevelPred < this.valueLevel) {
        this.upwardMovement = true;
        this.downwardMovement = false;
        setTimeout(() => this.upwardMovement = false, 4000);
      } else if (this.valueLevelPred > this.valueLevel) {
        this.downwardMovement = true;
        this.upwardMovement = false;
        setTimeout(() => this.downwardMovement = false, 4000);
      } else {
        return
      }
    },

    clearLocalStorage() {
      localStorage.removeItem("level");
      this.valueLevel = "1";
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  max-width: 1200px;
  max-height: 600px;
}

.btnGroup {
  display: flex;
  margin-top: 20px;
  margin-left: 100px;
}
</style>
