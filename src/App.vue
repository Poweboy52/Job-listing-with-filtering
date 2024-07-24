<template>
    <div class="page">
        <div class="filters-container">
            <input v-model="search" type="text"/>
            <div v-for="(checkbox, index) in conditions" :key="index">
                <Checkbox :label="checkbox.label" @checkboxTrigger="checkbox.active = $event"/>
            </div>
        </div>
        <JobLists :data="filteredList || data"/>
    </div>
</template>

<script setup>
    import data from "./assets/data.json"
    import JobLists from "./components/JobLists.vue";
    import { ref, computed } from "vue"
    import Checkbox from "./components/Checkbox.vue";
    const search = ref("")
    const filteredList = computed(() => {
        return data.filter((job) => {
            let validJob = true
            for (let checkbox in conditions) {
                if (checkbox.active && validJob) {
                    validJob = job.contract.includes(checkbox.label)
                }
            }
            if (validJob) {
                validJob = job.position.includes(search.value)
            }

            if (validJob) {
                return job
            }
        })
    })
    const conditions = ref([{
        label: "Full Time",
        active: "false"
        },
        {label: "Part Time",
        active: "false"
    }])
</script>

<style scoped>
    .page{
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
        background-color: hsl(180, 31%, 95%);
        gap: 32px;
        min-height: 100vh;
        padding: 20px 0px;
    }
    .filters-container{
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 900px;
    }
</style>