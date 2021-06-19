<template>
    <div class="item">
        {{ title }}
    </div>
</template>

<script>
export default {
    props: {
        title: String
    }
}
</script>

<style scoped lang='scss'>
.item {
    width: 100%;
    color: #666;
    background-color: #fff;
    border-bottom: 0.1px solid #ccc;
    line-height: 48px;
    cursor: pointer;
    transition: 0.2s;

    &:hover {
        color: #000;
        border-bottom: 1.1px solid #000;
    }
}
</style>