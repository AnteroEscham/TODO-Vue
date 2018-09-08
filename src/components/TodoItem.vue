<template>
    <li class="todo__item" :class="checked ? 'todo__item--completed' : ''">
        <div class="todo__check">
            <label class="todo__check-label">
                <input type="checkbox" v-model="checked" class="todo__check-input">
                <div @click="setStatus" class="todo__check-btn"></div>
            </label>
        </div>
        <div class="todo__name">{{ todo.text }}</div>
        <div @click="removeItem" class="todo__close"></div>
    </li>
</template>

<script>
export default {
    name: 'TodoItem',

    props: ['todo'],

    data() {
        return {
            checked: false
        }
    },

    methods: {
        removeItem() {
            return this.$store.dispatch('removeTodo', this.todo);
        },

        setStatus() {
            if (!this.checked) {
                return this.$store.dispatch('setTodoStatus', {
                    todo: this.todo,
                    status: 'done'
                });
            } else {
                return this.$store.dispatch('setTodoStatus', {
                    todo: this.todo,
                    status: 'active'
                });
            }
        }
    }
}
</script>
