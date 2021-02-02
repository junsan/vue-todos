<template>
    <div>
        <input v-model='item' type="text"> <button @click="addTodo">Add + </button>    
    </div>    
</template>

<script>
export default {
    name: "AddTodo",
    data() {
        return {
            item: ''
        }
    },
    methods: {
        addTodo() {
            this.$emit('add-item', this.item);
            console.log('added');
        }
    }
}
</script>

<style scoped>

</style>