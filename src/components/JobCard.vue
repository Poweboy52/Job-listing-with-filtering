<template>
    <div class="job-card">
        <div class="job-card-left">
            <div class="icon-container">
                <img class="icon-image" src="../assets/account.svg"/>
            </div>
            <div class="description">
                <div class="company-title">
                    <p class="company-name">{{ company }}</p>
                    <p v-if="props.new" class="new-text">new!</p>
                    <p v-if="featured" class="featured-text">featured</p>
                </div>
                <div>
                    <p class="role-name">{{ position }}</p>
                </div>
                <div class="job-details">
                    <p>{{ postedAt }}</p>
                    <p>{{ contract }}</p>
                    <p>{{ location }}</p>
                </div>
            </div>
        </div>
        <div class="tags-container">
            <div v-for="(tag, index) in [...languages, ...tools]" class="tag" :key="index">
                <p>{{ tag }}</p>
            </div>
        </div>
    </div>
</template>

<script setup>
    const props = defineProps({
        company: String,
        contract: String,
        featured: Boolean,
        id: Number,
        languages: Array,
        level: String,
        location: String,
        logo: String,
        new: Boolean,
        position: String,
        postedAt: String,
        role: String,
        tools: Array
    })
</script>

<style scoped>
    .job-card {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        gap: 10px;
        align-items: center;
        width: 900px;
        background-color: white;
        border-radius: 10px;
        padding: 8px 18px;
    }
    .job-card-left{
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        gap: 30px;
        align-items: center;
    }
    .description {
        display: flex;
        justify-content: space-between;
        flex-direction: column;
        gap: 5px;
        align-items: center;
    }
    .role-name{
        font-size: 14px
    }
    .company-title {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }
    .job-details {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }
    .tags-container {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        gap: 20px;
    }
    .tag{
        font-size: 14px;
    }
    .icon-image{
    height: 40%;
    width: auto;
    }
    .new-text{
        background-color: hsl(180, 8%, 52%);
        border-radius: 8px;
        padding: 2px 4px;
        color: white;
        text-transform: uppercase;
        font-size: 10px;
    }
    .featured-text{
        background-color: hsl(180, 14%, 20%);
        border-radius: 8px;
        padding: 2px 4px;
        color: white;
        text-transform: uppercase;
        font-size: 10px;
    }
</style>