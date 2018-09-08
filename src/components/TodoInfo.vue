<template>
    <div class="todo__info">
        <ul class="todo__info-list">
            <li class="todo__info-item">
                <box-icon class="todo__info-icon" name='task'></box-icon>
                <div class="todo__info-text">{{ todoCount }}</div>
            </li>
            <li class="todo__info-item">
                <box-icon class="todo__info-icon todo__info-icon--red" name='exclamation'></box-icon>
                <div class="todo__info-text">{{ todoCount - todoCountDone }}</div>
            </li>
            <li class="todo__info-item">
                <box-icon class="todo__info-icon todo__info-icon--green" name='check-double'></box-icon>
                <div class="todo__info-text">{{ todoCountDone }}</div>
            </li>
        </ul>
    </div>
</template>


<script>
export default {
    name: 'TodoInfo',

    props: ['todo'],

    computed: {
        todoCount() {
            return this.todo.length;
        },

        todoCountDone() {
            return this.todo.filter(e => e.status == 'done').length;
        }
    }
}
</script>
