<script lang="ts" setup>
// введенное значение
const input = defineModel();

// сообщение об ошибке
const error = ref("");

// валидация
const regex = /^\d+(\/\d+)*$/;
watch(input, () => {
    if (input.value && !regex.test(input.value as string)) error.value = "Введите число"
    else error.value = "";
})
</script>

<template>
    <div class="input-wrap">
        <input class="input" type="text" placeholder="Введите число" v-model.trim="input">
        <span class="error" v-if="error">{{ error }}</span>
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