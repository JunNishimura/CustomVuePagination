<template>
    <div class="pagination">
        <div class="item-list">
            <item v-for="(item, idx) in displayItems" :key="idx" :title="item" />
        </div>
        <div class="page-btns">
            <page-button @changePage="changePage" v-for="n in pageNum" 
                :key="n" 
                :pageNumber="n"
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
            curPage: 1, // curPage starts from 1
            pageNum: 0, // number os pages
        }
    },
    created() {
        this.calcPageNum();
    },
    computed: {
        displayItems() {
            const startIdx = (this.curPage - 1) * this.itemNumPerPage;
            const endIdx   = startIdx + this.itemNumPerPage;
            return this.items.slice(startIdx, endIdx);
        },
    },
    methods: {
        changePage(value) {
            this.curPage = value;
        },
        calcPageNum() {
            this.pageNum =  Math.ceil(this.items.length / this.itemNumPerPage);
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