<script>

let todos = [
  
]
var task = ""
const addTodo = (e) => {
 e.preventDefault()
  let newTodo = {
    date:new Date(),
    status:false,
    task:task
  }
  todos = [...todos,newTodo]
  task = ""
}
const completed = (i) => {
  todos[i].status = !todos[i].status
}
const del = (i) => { 
  let deleteTodo = todos[i]
  todos = todos.filter((item) => item != deleteTodo)
}
  $: console.log(todos)
  
</script>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-iYQeCzEYFbKjA/T2uDLTpkwGzCiq6soy8tYaI1GyVh/UjpbCx/TYkiZhlZB6+fzT" crossorigin="anonymous">

<form on:submit|preventDefault={addTodo}>
<input class="form-control" type="text" bind:value={task}>
  <input class="btn btn-outline-primary" type="submit">
</form>
<ol>
{#each todos as item,i}
<li class:status={item.status}>{item.task}</li>
  <button class="btn btn-outline-primary"  on:click={() => completed(i)}>📌</button>
  <button class="btn btn-outline-primary" on:click={() => del(i)}>❌</button>
{/each}
</ol>

<style>
.status{
text-decoration:line-through
}
  </style>