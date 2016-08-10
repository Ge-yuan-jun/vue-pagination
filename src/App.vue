<template>
    <pagination :total-page="total" :page-active.sync="pageActive"></pagination>
</template>
<script>
    import pagination from './components/pagination.vue'
    export default {
        data () {
            return {
                total: 20,
                pageActive: 1
            }
        },
        components: {
            pagination
        },
        watch: {
            pageActive () {
                // 页码发生改变时可以进行操作(一般用来改变页面的展示)
                console.log(1)
            }
        }
    }
</script>
<style>
    html {
        height: 100%;
    }

    body {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100%;
    }
</style>
