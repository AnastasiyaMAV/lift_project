<template>
  <button class="buttonClass"><slot></slot></button>
</template>

<script>
export default {
  name: "main-button",
};
</script>

<style scoped>
.buttonClass {
  width: 140px;
  height: 50px;
  border-width: 1px;
  color: whitesmoke;
  border-color: #4e6096;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
  box-shadow: 0px 0px 0px 2px #9fb4f2;
  text-shadow: 0px 1px 0px #283966;
  background: linear-gradient(rgb(9, 9, 121), #476e9e);
  font-size: 21px;
}

.buttonClass:hover {
  background: linear-gradient(#476e9e, rgb(120, 146, 194));
}
</style>
