<template>
    <pagination :total-page="total"></pagination>
</template>
<script>
    import pagination from './components/pagination.vue'
    export default {
        data () {
            return {
                total: 20
            }
        },
        components: {
            pagination
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
