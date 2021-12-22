<template>
<div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>{{ task.text }}
        <i class="fas fa-fatime" @click="onDelete(task.id)">X</i>
    </h3>
    <p>{{ task.date }}</p>
</div>
</template>

<script>
    export default {
        name: 'Task',
        props: {
            task: Object,
        },
        methods: {
          onDelete(id){
            this.$emit('delete-task', id)
          }
        }
    }
</script>

<style scope>
.fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 20px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>