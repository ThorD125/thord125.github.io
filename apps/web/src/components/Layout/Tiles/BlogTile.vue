<template>
    <div class="hover:cursor-pointer hover:text-accent hover:underline duration-300" @click="toggleDiv">
        <h2 class="flex">
            <p>{{ props.title }}</p>
            <p class="ml-2 text-base m-auto" v-if="props.date">- {{ props.date }}</p>
        </h2>
    </div>
    <div v-show="!showFirstDiv || props.download">
        <slot></slot>
    </div>
</template>

<script setup lang="ts">
    import { ref } from 'vue';

    interface IProps {
        title: string;
        date?: string;
        download?: boolean;
    }

    const props = withDefaults(defineProps<IProps>(), {});

    const showFirstDiv = ref(true);

    const toggleDiv = () => {
        showFirstDiv.value = !showFirstDiv.value;
    };
</script>

<style scoped>
    /* Your styles here */
</style>
