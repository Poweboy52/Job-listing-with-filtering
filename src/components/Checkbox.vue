<template>
    <div>
        <label>{{ label }}</label>
        <input type="checkbox" @change="handleChange()"/>
    </div>
</template>

<script setup>
    import { ref } from "vue"
    defineProps({
        label: String
    })
    const emit = defineEmits([
        "checkboxTrigger"
    ])
    const active = ref(false)
    function handleChange(){
        active.value = !active.value
        emit("checkboxTrigger", active.value)
    }
</script>

<style scoped>

</style>