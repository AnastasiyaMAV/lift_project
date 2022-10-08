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
    <label class="label" :for="level.id">{{ level.title }}</label>
  </div>
</template>

<script>
export default {
  props: {
    levels: {
      type: Array,
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
      setTimeout(() => this.ifDisabled = false, 1000);
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
</style>
