<template>
    <div class="todo__controls">
        <ul class="todo__states">
            <li @click.prevent="todoFilter('all', $event)" class="todo__state todo__state--active">All</li>
            <li @click.prevent="todoFilter('active', $event)" class="todo__state">Active</li>
            <li @click.prevent="todoFilter('done', $event)" class="todo__state">Completed</li>
        </ul>
        <a href="#" @click.prevent="clearCompleteTodo" class="todo__clear">Clear completed</a>
    </div>
</template>

<script>

export default {
    name: 'TodoControls',

    props: ['todo'],

    data() {
        return {
            activeFilter: ''
        }
    },

    methods: {
        clearCompleteTodo() {
            this.todo.forEach(e => {
                if (e.status == 'done') {
                    this.$store.dispatch('removeTodo', e);
                }
            });
        },

        todoFilter(type, event) {
            const elem = event.currentTarget;
            const prevElem = this.$el.querySelector('.todo__state--active');

            this.$emit('todoFilter', type);
            prevElem.classList.remove('todo__state--active');
            elem.classList.add('todo__state--active');
        }
    }
}

</script>
