<template>
  <div class="shaft">
    <lift-component
      :valueLevel="valueLevel"
      :upwardMovement="upwardMovement"
      :downwardMovement="downwardMovement"
    />
  </div>
</template>

<script>
import LiftComponent from "./LiftComponent.vue";
export default {
  components: { LiftComponent },

  props: {
    valueLevel: {
      type: String,
      required: true,
    },
    upwardMovement: {
      type: Boolean,
      required: true,
    },
    downwardMovement: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

<style scoped>
.shaft {
  width: 74px;
  height: 100vh;
  position: absolute;
  background: none;
  border-left: 1px solid grey;
  border-right: 1px solid grey;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
