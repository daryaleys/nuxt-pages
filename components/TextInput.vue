<script lang="ts" setup>
defineProps<{
  currentInput: string,
  label: string
}>()

// введенное значение
const input = defineModel();
</script>

<template>
    <div class="input-wrap">
        <label class="label" :for="currentInput">{{ label }}</label>
        <input class="input" type="text" v-model.lazy="input" :id="currentInput" >
    </div>
</template>

<style lang="scss" scoped>
.input-wrap {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 5px;
}

.error {
    color: red;
    font-weight: 500;
}
</style>