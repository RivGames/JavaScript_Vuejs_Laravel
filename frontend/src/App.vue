<script>
let id = 0;
export default {
    data() {
        return {
            name: "Ihor",
            profession: "Programmer",
            salary: "5000$",
            surname: "Rud",
            professionClass: "profession",
            countLikes: 0,
            text: "",
            paragraphClass: "p",
            address: "Ukraine,Kropivnitskiy",
            show: false,
            newTodo: '',
            todos: [
                {id: id++, text: "Learn Vue"},
                {id: id++, text: "Learn Laravel"},
            ],
        }
    },
    methods: {
        increment() {
            this.countLikes++;
        },
        toggle() {
            this.show = !this.show;
        },
        addTodo() {
            this.todos.push({id: id++,text:this.newTodo});
            this.newTodo = '';
        },
        removeTodo(todo) {
            this.todos = this.todos.filter((t) => t !== todo);
        },
    },
    mounted() {
      this.$refs.h3.textContent = 'NOT H3';
      this.$refs.heading4.classList = 'heading';
    }
}
</script>

<template>
    <h1>Your name {{ name }}</h1>
    <h2>Your surname {{ surname }}</h2>
    <h3>Your salary is: {{ salary }}</h3>
    <h1 :class="professionClass">{{ profession }}</h1>
    <button @click="increment">Likes {{ countLikes }}</button>
    <input v-model="text">
    <p v-bind:class="paragraphClass">{{ text }}</p>
    <button @click="toggle">Show/Hide address</button>
    <h2 v-if="show">{{ address }}</h2>
    <h1>Your todos:</h1>
    <form @submit.prevent="addTodo">
        <input v-model="newTodo">
        <button>Add todo</button>
    </form>
    <ul>
        <li v-for="todo in todos" v-bind:key="todo.id">
            {{ todo.text }}
            <button @click="removeTodo(todo)">X</button>
        </li>
    </ul>
    <h3 ref="h3">H3</h3>
    <h4 ref="heading4">H4</h4>
</template>

<style scoped>
.profession {
    color: greenyellow;
}

.p {
    color: chartreuse;
}
.heading{
    color: red;
}
</style>
