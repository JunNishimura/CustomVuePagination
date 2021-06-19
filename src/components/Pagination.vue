<template>
    <div class="pagination">
        <div class="item-list">
            <item v-for="(item, idx) in displayItems" :key="idx" :title="item" />
        </div>
        <div class="page-btns">
            <page-button @changePage="changePage" v-for="(pNum, idx) in pageNumbers" 
                :key="idx" 
                :pageNumber="pNum"
                :curPage="curPage"
            />
        </div>
    </div>
</template>

<script>
import Item from '@/components/Item.vue';
import PageButton from '@/components/PageButton.vue';

export default {
    components: {
        Item,
        PageButton
    },
    props: {
        items: Array,
        itemNumPerPage: Number,
    },
    data() {
        return {
            curPage: 2, // curPage starts from 1
        }
    },
    computed: {
        displayItems() {
            const startIdx = (this.curPage - 1) * this.itemNumPerPage;
            const endIdx   = startIdx + this.itemNumPerPage;
            return this.items.slice(startIdx, endIdx);
        },
        pageNumbers() {
            const lastPageNum = Math.ceil(this.items.length / this.itemNumPerPage)
            return Array.from({length: lastPageNum}, (_, i) => i+1); // [1, .. , N]
        }
    },
    methods: {
        changePage(value) {
            this.curPage = value;
        }
    }
}
</script>

<style scoped lang="scss">
.pagination {
    max-width: 640px;
    margin: 0 auto;

    .item-list {
        margin: 5rem 0;
    }

    .page-btns {
        display: flex;
        justify-content: center;
        align-items: center;
    }
}
</style>