<template>
  <div class="floor" v-for="level in levels" :key="level.id" :level="level">
    <input
      class="input"
      type="radio"
      :id="level.id"
      :value="level.title"
      v-model="floorLift"
      @click="elevatorMovement"
      :disabled="ifDisabled"
    />
    <label
      class="label"
      :class="{ textFlicker: valueLevel === level.title ? upwardMovement || downwardMovement : '' }"
      :for="level.id"
      >{{ level.title }}</label
    >
  </div>
</template>

<script>
export default {
  emits: ["movement"],
  props: {
    levels: {
      type: Array,
      required: true,
    },
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
  data() {
    return {
      floorLift: "",
      ifDisabled: false,
    };
  },
  methods: {
    elevatorMovement(event) {
      this.$emit("movement", event.target.value);
      this.ifDisabled = true;
      setTimeout(() => (this.ifDisabled = false), 4000);
    },
  },
};
</script>

<style scoped>
.floor {
  height: 115px;
  border-top: 1px solid grey;
  border-bottom: 1px solid grey;
}

.input {
  margin-left: 85px;
  margin-top: 45px;
}

.label {
  font-size: 21px;
}

.textFlicker {
  animation: flicker 0.6s 2;
}
@keyframes flicker {
  from {
    opacity: 1;
    color: red;
  }
  to {
    opacity: 0;
  }
}
</style>
