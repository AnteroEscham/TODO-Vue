<template>
    <div class="todo__block">
        <todoInput :type ="type"/>

        <ul class="todo__list">
                <draggable v-for="(todo, index) in todo" :key="index + todo.text">
                    <TodoItem
                    :todo="todo"
                    v-show="!showStatus || todo.status == showStatus"
                    />
                </draggable>
            
        </ul>

        <TodoControls @todoFilter="filterType" :todo="todo"/>
        <TodoInfo :todo="todo"/>
    </div>
</template>

<script>

import TodoInput from './TodoInput.vue';
import TodoControls from './TodoControls.vue';
import TodoItem from './TodoItem.vue';
import TodoInfo from './TodoInfo.vue';

export default {
    name: 'Todo',

    components: {
        TodoInput,
        TodoControls,
        TodoItem,
        TodoInfo
    },

    props: ['todo', 'type'],

    data() {
        return {
            showStatus: ''
        }
    },

    computed: {

    },

    methods: {
        filterType(status) {
            if (status == 'done') {
                this.showStatus = 'done';

            } else if (status == 'active') {
                this.showStatus = 'active';

            } else {
                this.showStatus = '';
            }
        }
    }

}

</script>

