<script>
    import TaskForm from "../../components/dashboard/TaskForm.svelte";
    import TaskList from "../../components/dashboard/TaskList.svelte";

    //state

    let taskInput = '';

    let taskList = [{
        text: "Buy sour straws",
        status: true
    }, {
        text: "Make spam musubi",
        status: false
    }];

    function addToList() {
        taskList = [
           { text: taskInput, status: true}, ...taskList
        ]
    }
</script>>

<div class="h-screen">
    <div class="flex min-h-full items-center justify-center py-12 px-4 sm:px-6 lg:px-8">
        <div class="w-full max-w-md space-y-16">
            <TaskForm taskInput={taskInput} add={addToList}/>
            <TaskList tasks={taskList} />
        </div>
    </div>
</div>
