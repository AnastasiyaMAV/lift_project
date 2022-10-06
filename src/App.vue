<template>
  <div class="app">
    <lift-shaft-component
      :valueLevel="valueLevel"
      :upwardMovement="upwardMovement"
      :downwardMovement="downwardMovement"
    />
    <floor-component :levels="levels" @movement="elevatorMovement" />
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
        { id: 7, title: "7" },
        { id: 6, title: "6" },
        { id: 5, title: "5" },
        { id: 4, title: "4" },
        { id: 3, title: "3" },
        { id: 2, title: "2" },
        { id: 1, title: "1" },
      ],
      valueLevel: 1,
      valueLevelPred: 1,
      upwardMovement: false,
      downwardMovement: false,
    };
  },

  methods: {
    elevatorMovement(value) {
      this.valueLevelPred = this.valueLevel;
      this.valueLevel = value;
      if (this.valueLevelPred < this.valueLevel) {
        this.upwardMovement = true;
        this.downwardMovement = false;
      } else {
        this.downwardMovement = true;
        this.upwardMovement = false;
      }
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
  max-width: 1400px;
  max-height: 840px;
}

</style>
