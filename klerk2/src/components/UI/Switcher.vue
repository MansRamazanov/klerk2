<template>
  <div v-if="props.size === 'small'">
    <label class="switch-s">
    <input type="checkbox" />
    <span class="slider-s round-s"></span>
  </label>
  </div>
  <div v-if="props.size === 'medium'">
    <label class="switch-m">
    <input type="checkbox" />
    <span class="slider-m round-m"></span>
  </label>
  </div>

</template>
<script setup lang="ts">
interface Props {
  size: String
}

const props = defineProps<Props>();

</script>
<style scoped>

/* SIZE SMALL */

.switch-s {
  position: relative;
  display: inline-block;
  width: 32px;
  height: 16px;
}

.switch-s input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider-s {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider-s:before {
  position: absolute;
  content: "";
  height: 14px;
  width: 14px;
 top: 1px;
 left: 1px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider-s {
  background-color: #2196f3;
}

input:focus + .slider-s {
  box-shadow: 0 0 1px #2196f3;
}

input:checked + .slider-s:before {
  -webkit-transform: translateX(16px);
  -ms-transform: translateX(16px);
  transform: translateX(16px);
}

.slider-s.round-s {
  border-radius: 16px;
}

.slider-s.round-s:before {
  border-radius: 50%;
}

/* SIZE MEDIUM */
.switch-m {
  position: relative;
  display: inline-block;
  width: 48px;
  height: 24px;
}

.switch-m input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider-m {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider-m:before {
  position: absolute;
  content: "";
  height: 22px;
  width: 22px;
 top: 1px;
 left: 1px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider-m {
  background-color: #2196f3;
}

input:focus + .slider-m {
  box-shadow: 0 0 1px #2196f3;
}

input:checked + .slider-m:before {
  -webkit-transform: translateX(23px);
  -ms-transform: translateX(23px);
  transform: translateX(23px);
}

.slider-m.round-m {
  border-radius: 34px;
}

.slider-m.round-m:before {
  border-radius: 50%;
}
</style>
