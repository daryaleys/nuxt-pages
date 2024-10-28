<script lang="ts" setup>

// вводимые значения
const numbers: Ref<number[]> = ref([]);

// максимальное количество полей ввода
const MAX_INPUT_LENGTH: number = 5;

// текущее количество полей на странице
const numbersLength: ComputedRef<number> = computed(() => (numbers.value.length + 1 <= MAX_INPUT_LENGTH ? numbers.value.length + 1 : numbers.value.length));

// результат сложения введенных значений
const result: ComputedRef<number> = computed(() => numbers.value.reduce((a, b) => (Number(a) + Number(b)), 0));

// const nextPage = () => navigateTo("/user");
</script>

<template>
    <form class="form">
        <NumberInput v-for="index in numbersLength" v-model="numbers[index - 1]" />
        <span v-if="numbers.length === MAX_INPUT_LENGTH && !isNaN(result)" class="result">Сумма: {{ result }}</span>
        <NuxtLink v-if="numbers.length === MAX_INPUT_LENGTH && !isNaN(result)" to="/user" class="btn">Далее</NuxtLink>
        <!-- <button v-if="numbers.length === MAX_INPUT_LENGTH && !isNaN(result)" type="submit" class="btn">Далее</button> -->
    </form>
</template>

<style lang="scss" scoped>
.result {
    font-size: 24px;
    font-weight: bold;
    align-self: flex-end;
    color: #4e584e;
}
</style>
