<template>
    <div>
        <TodoComp 
            v-for="todo in todos" 
            :key="todo.id" 
            :todo="todo"
            @toggle-checkbox="toggleCheckbox"
            @click-delete="deleteTodo"
        />
    </div>
</template>

<script>
import TodoComp from '@/components/TodoComp.vue';
export default {
    components: {
        TodoComp,
    },

    methods: {
        toggleCheckbox(value) {
            this.$emit('toggle-checkbox', value);
        },

        deleteTodo(todoId) {
            this.$emit('click-delete', todoId);
        },
    },

    computed: {
        todos (){
            return this.$store.state.todo.todos;
        },
    },
}
</script>

<style>

</style>