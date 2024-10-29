<script lang="ts" setup>
const opened = defineModel();
</script>

<template>
    <div class="modal-container">
        <div class="modal">
            <slot />
        </div>
    </div>
</template>

<style lang="scss" scoped>
.modal-container {
    position: fixed;
    inset: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.3);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 10;
}

.modal {
    padding: 50px;
    border-radius: 10px;
    background: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
}
</style>