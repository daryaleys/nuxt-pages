<script lang="ts" setup>
type UserData = {
    surname: string;
    name: string;
};

const inputLabels: Record<keyof UserData, string> = {
    surname: "Фамилия",
    name: "Имя",
};

const userValues: UserData = {
    surname: "",
    name: "",
};

const currentInput: Ref<keyof UserData | ""> = ref("");

const changeStep = () => {
    if (!currentInput.value) currentInput.value = "surname";
    else currentInput.value = "name";
};

const setResult = () => {
    console.log(userValues);
};
</script>

<template>
    <form class="form">
        <TextInput v-if="currentInput" v-model="userValues[currentInput]" :currentInput :label="inputLabels[currentInput]" />
        <button v-if="currentInput === 'name'" @click.prevent="setResult" type="submit" class="btn">Отправить</button>
        <button v-else @click.prevent="changeStep" class="btn">Далее</button>
    </form>
</template>

<style lang="scss" scoped></style>
