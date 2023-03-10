<script>
    export let tasks;
</script>

<div class='rounded-lg shadow-lg p-8 flex flex-col gap-4'>
    {#each tasks as item,index}
    <div class='rounded-md p-4 justify-between flex flex-row border-gray-800 border-2'>
        <div class='font-medium text-sm'>{item.text}</div>
        <button class>x</button>
    </div>
    {/each}
</div>