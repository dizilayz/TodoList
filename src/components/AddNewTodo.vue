<template>
    <div>
        <input v-model="localInput" type="text">
        <button @click="addNewTodo" type="button" class="btn">Add</button>
    </div>
</template>

<script>
    export default {
        data:() => ({
            localInput: '',
        }),
        methods: {
            addNewTodo: function() {
                this.$emit('add-new-todo', this.localInput);
                this.localInput = '';
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>