<template>
    <div class="home">
        <pagination 
            :items="items"
            :itemNumPerPage="10"
        />
    </div>
</template>

<script>
import Pagination from '@/components/Pagination.vue';

export default {
    components: {
        Pagination
    },
    data() {
        return {
            items: [],
        }
    },
    created() {
        // itemの作成
        for (let i = 1; i <= 25; i++) {
            this.items.push(`Item ${i}`);
        }
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
</style>