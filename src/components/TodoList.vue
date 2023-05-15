<template>
    <li class="list-group-item">

        <span
            :class="[todo.completed ? 'lined' : '']">{{
                todo.id }}. {{ todo.title }}</span>
        <input @change="isChecked" type="checkbox"
            class="list-group-input"
            :checked="todo.completed">
        <button @click="removeTodo" type="button"
            class="btn btn-danger">Remove</button>
    </li>
</template>

<script>

export default {
    data: () => ({

    }),
    components: {

    },
    props: {
        todo: {
            type: Object,
            required: true,
        },
        index: {
            type: Number,
            required: true,
        }
    },
    methods: {
        isChecked: function () {
            this.$emit('is-checked', this.index);
        },
        removeTodo: function() {
            this.$emit('remove-todo', this.index);
        }
    }
}
</script>

<style scoped>
.list-group-item {
    width: fit-content;
}

.lined {
    text-decoration: line-through;
}

.list-group-input {
    margin-left: 5px;
    margin-right: 5px;
}</style>