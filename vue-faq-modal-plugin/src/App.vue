<script setup>
import { ref, inject } from "vue"

const modals = inject("$modals")
const result = ref("")

function showModal() {
    result.value = "";
    modals.show("myModal").then(() => {
        result.value = "Modal accepted"
    }, () => {
        result.value = "Modal cancelled"
    })
}

</script>

<template>
    <div class="app">
        <button @click="showModal">
            Show modal
        </button>
        <div>{{result}}</div>
        <Modal name="myModal" title="Modal example">
            Some important content here
        </Modal>
    </div>
</template>

<style scoped>
.app {
    width: 100vw;
    min-height: 100vh;
    padding: 0;
}
</style>
