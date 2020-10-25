<template>
    <div>这是UserDetail
        {{ id }}
    </div>
</template>

<script>
export default {
    name: "UserDetail",
    data(){
        return {
            id:""
        }
    },
    created() {
        this.id = this.$route.params.id
        // console.log(this.info)
    }
}
</script>

<style scoped>

</style>
