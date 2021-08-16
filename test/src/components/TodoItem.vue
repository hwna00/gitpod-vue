<template>
    <div class="lists">
        <ul>
            <li v-for="(todo, index) in todos" :key="index">
                {{ todo }}
                <span @click="removeItem(index)">삭제</span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: ['todos'],
    methods: {
        removeItem(index) {
            this.todos.splice(index, 1);
            localStorage.setItem("todos", JSON.stringify(this.todos));
        }
    }
}
</script>