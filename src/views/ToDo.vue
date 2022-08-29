<script>
import { ref } from 'vue'

export default {
  setup() {
    // declaring data - curly brackets mean one array
    const todos = ref([
        {
            text: "First todo",
            createdAt: "28-08-2022"
        },
        {
            text: "Second todo",
            createdAt: "29-08-2022"
        },
        {
            text: "Third todo",
            createdAt: "30-08-2022"
        }
        
    ])

    // returning data to the page
    return {
        todos
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
                        class="p-8 bg-purple-200 shadow-md rounded flex items-center justify-between">
                        <div>
                            <div class="text-purple-800"> {{ todo.text }} </div>
                            <div class="text-purple-800 text-sm"> {{ todo.createdAt }} </div>
                        </div>
                        <div class="space-x-2">
                            <button class="px-2 text-red-600" title="Remove todo">
                                &times;
                            </button>
                            <button class="px-2 text-red-600" title="Mark as done">
                                &check;
                            </button>
                            <button class="px-2 text-red-600" title="Mark as undone">
                                &#8630;
                            </button>
                        </div>
                    </div>
                    <!-- end of Todo item -->

                    <div class="px-8 py-10 bg-purple-200 text-purple-800 shadow-md rounded text-sm">
                        You don't have any taks to do.
                    </div>

                </div>

                <div class="col-span-6">
                    <div class="p-8 bg-purple-200 text-purple-800 shadow-md rounded">
                        <h2 class="text-xl"> Add a todo </h2>
                        <input type="text" class="p-2 mt-4 bg-purple-100 text-purple-800 border rounded w-full">
                    </div>
                </div>

            </div>
        </div>
    </div>

</template>