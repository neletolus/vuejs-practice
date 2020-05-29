<template>
    <div class="todo-item">
        <li>
            {{todo.text}}
        </li>
    </div>
</template>

<script>
    export default {
        name: "todo-item",
        props: ['todo'],
        data() {
            return {
                todos: [
                    {id: 1, text: "apple"},
                    {id: 2, text: "banana"},
                    {id: 3, text: "orange"}
                ]
            }
        },
    }
</script>

<style scoped>

</style>
