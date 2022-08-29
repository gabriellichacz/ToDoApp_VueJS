<script>
import { ref, reactive } from 'vue'

export default {
  setup() {
    // declaring data

    // todos data curly brackets mean one array
    const todos = reactive([]);
    
    // new todo creation
    const todoText = ref("");

    function addTodo() {
        todos.unshift({ // unshift adds data to an existing array at the beginning
            text: todoText.value, // because the data is const todoText = {value: ""}
            createdAt: new Date(),
            done: false,
        });

        todoText.value = "";
    };

    function markAsDone(index) {
        todos[index].done = true;
    }

    function markAsUnDone(index) {
        todos[index].done = false;
    }

    function removeTodo(index) {
        // Default confirmation
        if (!confirm("Are you sure?")) {
            return;
        }
        todos.splice(index, 1) // Deleting todos[index]
    }


    // returning data to the page
    return {
        todos,
        todoText,
        addTodo,
        markAsDone,
        markAsUnDone,
        removeTodo,
    }
  },
}
</script>

<template>

    <div class="container mx-auto">
        <h1 class="mt-8 text-2xl text-center text-purple-100"> To do page </h1>
        <div class="mt-3">
            <div class="grid grid-cols-12 gap-4">
                <div class="col-span-6 space-y-4 overflow-y-auto px-1" style="height: 500px">
                    
                    <!-- Todo item -->
                    <div v-for="(todo, index) in todos"
                        class="p-8 bg-purple-200 shadow-md rounded flex items-center justify-between"
                        :class="{'bg-green-200': todo.done}">
                        <div>
                            <div class="text-purple-800 mb-5"> {{ todo.text }} </div>
                            <div class="text-purple-800 text-sm"> {{ todo.createdAt.toString() }} </div>
                        </div>
                        <div class="space-x-2">
                            <button @click="removeTodo(index)" 
                                class="px-2 text-red-600" title="Remove todo">
                                &times;
                            </button>
                            <button v-if="!todo.done" @click="markAsDone(index)"
                                class="px-2 text-green-600" title="Mark as done">
                                &check;
                            </button>
                            <button v-else @click="markAsUnDone(index)" 
                                class="px-2 text-yellow-600" title="Mark as undone">
                                &#8630;
                            </button>
                        </div>
                    </div>
                    <!-- end of Todo item -->

                    <div v-if="todos.length == 0" class="px-8 py-10 bg-purple-200 text-purple-800 shadow-md rounded text-sm">
                        You don't have any taks to do.
                    </div>

                </div>

                <div class="col-span-6">
                    <div class="p-8 bg-purple-200 text-purple-800 shadow-md rounded">
                        <h2 class="text-xl"> Add a todo </h2>
                        <!-- enter key adds todo-->
                        <input type="text" v-model="todoText" @keydown.enter="addTodo"
                            class="p-2 mt-4 bg-purple-100 text-purple-800 border rounded w-full">
                    </div>
                </div>

            </div>
        </div>
    </div>

</template>