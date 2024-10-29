<script lang="ts" setup>
const userInfo = useState('userInfo')
</script>

<template>
    <div class="info-wrap" v-if="userInfo">
        <h1>Информация</h1>
        <span class="info-text">Фамилия: {{ userInfo.surname }}</span>
        <span class="info-text">Имя: {{ userInfo.name }}</span>
        <span class="info-text">Телефон: {{ userInfo.phone }}</span>
    </div>
    <NuxtLink v-else to="/user" class="btn">Ввести данные</NuxtLink>
</template>

<style lang="scss" scoped>
.info-wrap {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
}

.info-text {
    font-size: 20px;
}
</style>