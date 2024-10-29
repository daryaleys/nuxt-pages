<script lang="ts" setup>
type UserData = {
    surname: string;
    name: string;
    phone: string;
};

const inputLabels: Record<keyof UserData, string> = {
    surname: "Фамилия",
    name: "Имя",
    phone: "Телефон"
};

const userInfo = useState('userInfo', () => ({
    surname: "",
    name: "",
    phone: "",
}))

const currentInput: Ref<keyof UserData | ""> = ref("");
let openModal = ref(false);

const changeStep = () => {
    if (!currentInput.value) currentInput.value = "surname";
    else if (currentInput.value === 'surname') currentInput.value = "name"
    else {
        currentInput.value = "phone";
        openModal.value = true;
    }
}
</script>

<template>
    <form class="form">
        <TextInput v-if="currentInput" v-model="userInfo[currentInput]" :currentInput
            :label="inputLabels[currentInput]" />

        <Modal v-if="openModal">
            <TextInput v-model="userInfo[currentInput]" :currentInput :label="inputLabels[currentInput]" />
            <NuxtLink to="/info" class="btn">Закончить</NuxtLink>
        </Modal>

        <button v-else @click.prevent="changeStep" class="btn">Далее</button>
    </form>
</template>

<style lang="scss" scoped></style>
