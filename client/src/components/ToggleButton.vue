<template>
    <label class="switch">
        <input tabindex="0" type="checkbox" @click="(e:Event) => toggle(e)">
        <span class="slider round"></span>
    </label>

</template>

<style scoped lang="css">
.switch {
    position: relative;
    display: inline-block;
    width: 160px;
    height: 34px;
}

/* Hide default HTML checkbox */
.switch input {
    opacity: 0;
    width: 0;
    height: 0;
}

/* The slider */
.slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #ccc;
    -webkit-transition: .4s;
    transition: .4s;
}

.slider:before {
    position: absolute;
    content: "";
    height: 26px;
    width: 26px;
    left: 4px;
    bottom: 4px;
    background-color: white;
    -webkit-transition: .4s;
    transition: .4s;
}

input:checked+.slider {
    background-color: var(--text-color);;
}

input:focus+.slider {
    box-shadow: 0 0 1px var(--text-color);;
}

input:checked+.slider:before {
    -webkit-transform: translateX(26px);
    -ms-transform: translateX(26px);
    transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
    border-radius: 34px;
}

.slider.round:before {
    border-radius: 50%;
}
</style>


<script setup lang="ts">

import { ref } from 'vue'

const emit = defineEmits(['updated']);


function toggle(event: Event) {
  emit('updated', event.target.value);
}
</script>