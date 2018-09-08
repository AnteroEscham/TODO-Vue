<template>
    <div class="todo__add">
        <input @keypress.enter="inputEnterTodo" v-model="message" type="text" placeholder="What need to be done?" class="todo__input">
        <button @click="inputEnterTodo" class="todo__enter">{{ message ? 'ENTER' : '...' }}</button>
    </div>
</template>

<script>

export default {
    name: 'TodoInput',

    props: ['type'],

    data() {
        return {
            message: ''
        }
    },

    methods: {
        inputEnterTodo() {
            if (this.message) {

                this.$store.dispatch('addTodo', {
                type: this.type,
                text: this.message,
                status: 'active'
                })
            }

            this.message = '';
        }
    }
}

</script>
