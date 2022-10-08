<template>
  <div
    class="lift"
    :class="{
      moov: upwardMovement || downwardMovement,
      moovUp: upwardMovement,
      moovDown: downwardMovement,
    }"
    :style="{ marginTop: -115 * valueLevel + 'px' }"
  >
    <div>Этаж {{ valueLevel }}</div>
    <div v-if="upwardMovement">&#9650;</div>
    <div v-else>&#9660;</div>
  </div>
</template>

<script>
export default {
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
.lift {
  position: relative;
  width: 70px;
  height: 115px;
  z-index: 9;
  border: 1px solid blue;
  border-radius: 2px;
  background: rgb(2, 0, 36);
  background: linear-gradient(
    90deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(9, 9, 121, 1) 35%,
    rgba(0, 212, 255, 1) 100%
  );
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: whitesmoke;
  font-size: 21px;
  top: 575px;
}

.moov {
  -webkit-transition: all 1s linear;
  -moz-transition: all 1s linear;
  transition: all 1s linear;
}

.moovUp,
.moovDown {
  animation-name: blink;
  animation-timing-function: linear;
  animation-delay: 1s;
  animation-duration: 1s;
  animation-iteration-count: 3;
}

@keyframes blink {
  50% {
    opacity: 0;
  }
}
</style>
