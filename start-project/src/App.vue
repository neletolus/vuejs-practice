<template>
    <div id="app">
        <h2>宣言的レンダリング</h2>
        <p>
            {{message}}
        </p>
        <h2>バインド</h2>
        <button v-on:click="change">赤くする</button>
        <p v-bind:class={red:isActive}>
            ボタンでバインドしたクラスがついたりきえたりするよ
        </p>
        <h2>条件分岐とループ</h2>
        <button v-on:click="hide">消す</button>
        <p v-if="seen">
            Now you see me
        </p>
        <ol>
            <todoItem
                    v-for="item in todos"
                    v-bind:todo="item"
                    v-bind:key="item.id"
            ></todoItem>
        </ol>
        <h2>ユーザー入力制御</h2>
        <button v-on:click="reverseMessage">メッセージを反転する</button>
        <h2>双方向バインディング</h2>
        <input v-model="message">
    </div>
</template>

<script>
    import todoItem from "./components/todo-item"

    export default {
        name: 'App',
        components: {
            todoItem
        },
        data() {
            return {
                message: "Hello World !!!!",
                isActive: true,
                seen: true,
                todos: [
                    {id: 1, text: "apple"},
                    {id: 2, text: "banana"},
                    {id: 3, text: "orange"}
                ]
            }
        },
        mounted() {
            this.todos.push({id: 4, text: "プッシュで追加できるよ"})
        },
        methods: {
            change() {
                this.isActive = !this.isActive;
            },
            hide() {
                this.seen = !this.seen;
            },
            reverseMessage() {
                this.message = this.message.split('').reverse().join('')
            }
        }
    }
</script>

<style>
    #app {

        max-width: 50%;
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin: 60px auto auto;
    }

    .red {
        background-color: red;
        color: white;
    }
</style>
