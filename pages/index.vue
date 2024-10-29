<script lang="ts" setup>

// вводимые значения
const numbers: Ref<number[]> = ref([]);

// максимальное количество полей ввода
const MAX_INPUT_LENGTH: number = 5;

// текущее количество полей на странице
const numbersLength: ComputedRef<number> = computed(() => (numbers.value.length + 1 <= MAX_INPUT_LENGTH ? numbers.value.length + 1 : numbers.value.length));

const division = (a: number) => {
    const digits = a.toString().split('/');
    return +digits[0] / +digits[1];
}

// результат сложения введенных значений
const result: ComputedRef<number> = computed(() => (
    numbers.value.reduce((a, b) => {
        if (isNaN(Number(a))) a = division(a);
        if (isNaN(Number(b))) b = division(b);
        return (Number(a) + Number(b));
    }, 0)
))
</script>

<template>
    <form class="form">
        <NumberInput v-for="index in numbersLength" v-model="numbers[index - 1]" />
        <span v-if="numbers.length === MAX_INPUT_LENGTH" class="result">
            Сумма: {{ result.toFixed(1) }}
        </span>
        <NuxtLink v-if="numbers.length === MAX_INPUT_LENGTH" to="/user" class="btn">Далее</NuxtLink>
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
