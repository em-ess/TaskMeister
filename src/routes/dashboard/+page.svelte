<script>
    import TaskForm from "../../components/dashboard/TaskForm.svelte";
    import TaskList from "../../components/dashboard/TaskList.svelte";

    //state

    let taskInput = '';

    let taskList = [
        {
            text: "Buy sour straws",
            status: true
        }, {
            text: "Make spam musubi",
            status: false
        }
    ];

    function addToList() {
        taskList = [
           { text: taskInput, status: true}, ...taskList
        ];
        taskInput = '';
    }

    function removeFromList(i) {
        taskList.splice(i,1);
        taskList = taskList;
    }
</script>

<div class="h-screen">
    <div class="flex min-h-full items-center justify-center py-12 px-4 sm:px-6 lg:px-8">
        <div class="w-full max-w-md space-y-16">
            <div>
                <h2 class="mt-6 text-center text-3xl font-bold tracking-tight text-gray-900">Task Meister</h2> 
            </div>
            <form 
                class="mt-8 space-y-6" 
                on:submit={(e) => {
                    e.preventDefault();
                    addToList();
                }}
            >
                <input type="hidden" name="remember" value="true">
                <div class="-space-y-px rounded-md shadow-sm">
                    <div>
                        <label for="task-input" class="sr-only">Task</label>
                        <input bind:value={taskInput} id="task-input" name="task-input" type="text" required class="relative block w-full rounded-t-md border-0 py-1.5 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:z-10 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" placeholder="What do you need to do?">
                    </div>
                </div>
                <div>
                    <button type="submit" class="group relative flex w-full justify-center rounded-md bg-indigo-600 py-2 px-3 text-sm font-semibold text-white hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">
                        Add Task
                    </button>
                </div>
            </form>
            <TaskList tasks={taskList} remove ={removeFromList}/>
        </div>
    </div>
</div>
